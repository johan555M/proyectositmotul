<template>
	<div class="text-center" style=" background-color:rgb(135,206,250)">
		

		<!-- Tarjetas -->
		<div class="flex justify-center " >
			
			

			<!-- Segunda columna (dos tarjetas una debajo de la otra) -->
			<div class="w-3/6 grid grid-cols-1 gap-2 ">
				<div v-for="(data, index) in infoGeneral" :key="index"
					class="bg-gradient-to-r  to-gray-200 p-3 rounded-lg mb-5">
					<div class="bg-sky-700 p-4 shadow-md rounded-md">
						<p class="mb-2 px-3 text-cyan-50 font-bold text-3xl">
							{{ calcularPorcentaje(data.alEvaluados, data.alTotal) }} % <i class="fas fa-clipboard-list"></i>
						</p>
						<p class="font-semibold">Hay {{ totalEvaluados }} alumnos que han resuelto la evaluación de un total de {{
							totalAlumnos }} alumnos</p>


					</div>
				</div>

				<div v-for="(data, index) in infoGeneral" :key="index"
					class="bg-gradient-to-r  to-gray-200 p-3 rounded-lg mb-5">
					<div class="bg-sky-600 p-4 shadow-md rounded-md">
						<p class="b-2 px-3 text-cyan-50 font-bold text-3xl">
							{{ calcularPorcentajeFaltante(data.alEvaluados, data.alTotal) }} % <i
								class="fas fa-exclamation-triangle text-red-500"></i>
						</p>
						<p class="font-semibold">
							Alumnos faltantes por evaluar: {{ data.alTotal - data.alEvaluados }} de {{ data.alTotal }}
						</p>
					</div>
				</div>
			</div>
		</div>



		
		
	</div>
</template>

<script setup>
import { onMounted } from 'vue'
import { ref } from 'vue'

// Definir variables reactivas
const infoGeneral = ref([]) // Almacena datos de Información General
const infoPersonal = ref([]) // Almacena datos de Información Personal

// Variables para mostrar en la plantilla
const totalEvaluados = ref(0)
const totalAlumnos = ref(0)
const periodo = ref('')

// Función para obtener datos de la API
async function fetchData(apiUrl, infoArray) {
	try {
		const response = await fetch(apiUrl)
		const data = await response.json()
		infoArray.value.push(data) // Almacenar datos en el array correspondiente

		// Actualizar variables para mostrar en la plantilla
		totalEvaluados.value += data.alEvaluados || 0
		totalAlumnos.value += data.alTotal || 0
		if (!periodo.value) {
			periodo.value = data.periodo || ''
		}

		console.log('Datos recibidos:', data)
		// Imprimir datos adicionales en la consola
		if (data.ObjectIE) {
			console.log('ObjectIE:', data.ObjectIE)
		}
		if (data.IEM) {
			console.log('IEM:', data.IEM)
		}
		if (data.IER) {
			console.log('IER:', data.IER)
		}
		if (data.II) {
			console.log('II:', data.II)
		}
		if (data.ISC) {
			console.log('ISC:', data.ISC)
		}
	} catch (error) {
		console.error('Error al obtener datos:', error)
	}
}

// Función que se ejecuta al montar el componente
onMounted(async () => {
	// Obtener datos de la primera API
	await fetchData('https://sitmotul.com.mx/api/statusEval', infoGeneral)

	// Obtener datos de la segunda API (puedes cambiar la URL según sea necesario)
	await fetchData('https://sitmotul.com.mx/api/statusEvalIng', infoPersonal)
})

// Función para calcular las horas y días restantes hasta la fecha y hora indicada
const calcularHorasRestantes = (fechaFin) => {
	const ahora = new Date();
	const fechaFinalizacion = new Date(fechaFin);
	const diferenciaTiempo = fechaFinalizacion - ahora;

	const diferenciaDias = Math.floor(diferenciaTiempo / (1000 * 60 * 60 * 24));
	const diferenciaHoras = Math.floor(diferenciaTiempo / (1000 * 60 * 60));

	return {
		dias: diferenciaDias >= 0 ? diferenciaDias : 0,
		horas: diferenciaHoras >= 0 ? diferenciaHoras : 0,
	};
};

// Función para calcular el porcentaje
const calcularPorcentaje = (evaluados, total) => {
	if (total === 0) {
		return 0;
	}
	return ((evaluados / total) * 100).toFixed(2);
};

// Función para calcular el porcentaje de los evaluados que faltan
const calcularPorcentajeFaltante = (evaluados, total) => {
	const faltantes = total - evaluados;
	if (total === 0 || faltantes <= 0) {
		return 0;
	}
	return ((faltantes / total) * 100).toFixed(2);
};



// Función para obtener la fecha actual en el formato deseado
const obtenerFechaActual = () => {
	const opcionesFecha = {
		weekday: "long",
		day: "numeric",
		month: "long",
		year: "numeric",
	};
	const fechaActual = new Date();
	return fechaActual.toLocaleDateString("es-MX", opcionesFecha);
};
</script>

