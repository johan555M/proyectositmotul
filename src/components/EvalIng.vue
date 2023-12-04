<script setup>

import { onMounted } from 'vue';
import { ref } from 'vue';

const infoi = ref('');
var IEML = "";
var IEMF = "";
var IIL = "";
var IIF = "";
var ISCL = "";
var ISCF = "";
var IEL = "";
var IEF = "";
var IERL = "";
var IERF= "";

async function fetchData() {
  try {
    const response = await fetch('https://sitmotul.com.mx/api/statusEvalIng')
    const data = await response.json();
    infoi.value = data
    // isLoading.value = false

    // IEM
    IEML = infoi.value['IEM'] ['listas'];
    IEMF = infoi.value['IEM'] ['faltantes'];
    document.getElementById('IEML').textContent = "Al día de hoy se han realizado " + IEML + " evaluaciones";
    document.getElementById('IEMF').textContent = "Faltan por realizarse " + IEMF + " evaluaciones";

    //II
    IIL = infoi.value['II'] ['listas'];
    IIF = infoi.value['II'] ['faltantes'];
    document.getElementById('IIL').textContent = "Al día de hoy se han realizado " + IIL + " evaluaciones";
    document.getElementById('IIF').textContent = "Faltan por realizarse " + IIF + " evaluaciones";

    //ISC
    ISCL = infoi.value['ISC'] ['listas'];
    ISCF = infoi.value['ISC'] ['faltantes'];
    document.getElementById('ISCL').textContent = "Al día de hoy se han realizado " + ISCL + " evaluaciones";
    document.getElementById('ISCF').textContent = "Faltan por realizarse " + ISCF + " evaluaciones";

    //IER
    IERL = infoi.value['IER'] ['listas'];
    IERF = infoi.value['IER'] ['faltantes'];
    document.getElementById('IERL').textContent = "Al día de hoy se han realizado " + IERL + " evaluaciones";
    document.getElementById('IERF').textContent = "Faltan por realizarse " + IERF + " evaluaciones";

   //IE
    IEL = infoi.value['IE'] ['listas'];
    IEF = infoi.value['IE'] ['faltantes'];
    document.getElementById('IEL').textContent = "Al día de hoy se han realizado " + IEL + " evaluaciones";
    document.getElementById('IEF').textContent = "Faltan por realizarse " + IEF + " evaluaciones";

    console.log(IEML);
  } catch (error) {
    console.error('Error al obtener datos:', error);
  }
}

onMounted(() => {
  fetchData();
})

</script>



<template>
  <div class="w-full flex flex-row gap-x-5 px-60 fonddown">
    <div class="flex flex-col w-1/3 gap-y-5 fond">
      <!-- IE -->
      <div class="w-full flex flex-col gap-y-3 border-2 rounded border-black px-3 py-1 shadow-lg">
        <h1 class="text-center text-2xl font-bold ">Ingeniería Electrónica</h1>
        <div class="w-full flex flex-col gap-y-1">
          <div class="w-full flex flex-row gap-x-1 items-center">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
              stroke="currentColor" class="w-12 h-12">
              <path stroke-linecap="round" stroke-linejoin="round"
                d="M11.35 3.836c-.065.21-.1.433-.1.664 0 .414.336.75.75.75h4.5a.75.75 0 00.75-.75 2.25 2.25 0 00-.1-.664m-5.8 0A2.251 2.251 0 0113.5 2.25H15c1.012 0 1.867.668 2.15 1.586m-5.8 0c-.376.023-.75.05-1.124.08C9.095 4.01 8.25 4.973 8.25 6.108V8.25m8.9-4.414c.376.023.75.05 1.124.08 1.131.094 1.976 1.057 1.976 2.192V16.5A2.25 2.25 0 0118 18.75h-2.25m-7.5-10.5H4.875c-.621 0-1.125.504-1.125 1.125v11.25c0 .621.504 1.125 1.125 1.125h9.75c.621 0 1.125-.504 1.125-1.125V18.75m-7.5-10.5h6.375c.621 0 1.125.504 1.125 1.125v9.375m-8.25-3l1.5 1.5 3-3.75">
              </path>
            </svg>
            <h2  Id="IEL"></h2>
          </div>

          <div class="w-full flex flex-row gap-x-1 items-center">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
              stroke="currentColor" class="w-12 h-12">
              <path stroke-linecap="round" stroke-linejoin="round"
                d="M12 9v3.75m9-.75a9 9 0 11-18 0 9 9 0 0118 0zm-9 3.75h.008v.008H12v-.008z"></path>
            </svg>
            <h2 Id="IEF"></h2>
          </div>

         
        </div>
      </div>

      <!-- II -->
      <div class="w-full flex flex-col gap-y-3 border-2 rounded border-black px-3 py-1 shadow-lg">
        <h1 class="text-center text-2xl font-bold">Ingeniería Industrial</h1>
        <div class="w-full flex flex-col gap-y-1">
          <div class="w-full flex flex-row gap-x-1 items-center">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
              stroke="currentColor" class="w-12 h-12">
              <path stroke-linecap="round" stroke-linejoin="round"
                d="M11.35 3.836c-.065.21-.1.433-.1.664 0 .414.336.75.75.75h4.5a.75.75 0 00.75-.75 2.25 2.25 0 00-.1-.664m-5.8 0A2.251 2.251 0 0113.5 2.25H15c1.012 0 1.867.668 2.15 1.586m-5.8 0c-.376.023-.75.05-1.124.08C9.095 4.01 8.25 4.973 8.25 6.108V8.25m8.9-4.414c.376.023.75.05 1.124.08 1.131.094 1.976 1.057 1.976 2.192V16.5A2.25 2.25 0 0118 18.75h-2.25m-7.5-10.5H4.875c-.621 0-1.125.504-1.125 1.125v11.25c0 .621.504 1.125 1.125 1.125h9.75c.621 0 1.125-.504 1.125-1.125V18.75m-7.5-10.5h6.375c.621 0 1.125.504 1.125 1.125v9.375m-8.25-3l1.5 1.5 3-3.75">
              </path>
            </svg>
            <h2 Id="IIL"></h2>
          </div>

          <div class="w-full flex flex-row gap-x-1 items-center">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
              stroke="currentColor" class="w-12 h-12">
              <path stroke-linecap="round" stroke-linejoin="round"
                d="M12 9v3.75m9-.75a9 9 0 11-18 0 9 9 0 0118 0zm-9 3.75h.008v.008H12v-.008z"></path>
            </svg>
            <h2 Id="IIF"></h2>
          </div>
        </div>
      </div>
    </div>

    <div class="flex flex-col w-1/3 gap-y-5">
      <!-- ISC -->
      <div class="w-full flex flex-col gap-y-3 border-2 rounded border-black px-3 py-1 shadow-lg">
        <h1 class="text-center text-2xl font-bold">Ingeniería en Sistemas</h1>
        <div class="w-full flex flex-col gap-y-1">
          <div class="w-full flex flex-row gap-x-1 items-center">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
              stroke="currentColor" class="w-12 h-12">
              <path stroke-linecap="round" stroke-linejoin="round"
                d="M11.35 3.836c-.065.21-.1.433-.1.664 0 .414.336.75.75.75h4.5a.75.75 0 00.75-.75 2.25 2.25 0 00-.1-.664m-5.8 0A2.251 2.251 0 0113.5 2.25H15c1.012 0 1.867.668 2.15 1.586m-5.8 0c-.376.023-.75.05-1.124.08C9.095 4.01 8.25 4.973 8.25 6.108V8.25m8.9-4.414c.376.023.75.05 1.124.08 1.131.094 1.976 1.057 1.976 2.192V16.5A2.25 2.25 0 0118 18.75h-2.25m-7.5-10.5H4.875c-.621 0-1.125.504-1.125 1.125v11.25c0 .621.504 1.125 1.125 1.125h9.75c.621 0 1.125-.504 1.125-1.125V18.75m-7.5-10.5h6.375c.621 0 1.125.504 1.125 1.125v9.375m-8.25-3l1.5 1.5 3-3.75">
              </path>
            </svg>
            <h2 Id="ISCL"></h2>
          </div>

          <div class="w-full flex flex-row gap-x-1 items-center">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
              stroke="currentColor" class="w-12 h-12">
              <path stroke-linecap="round" stroke-linejoin="round"
                d="M12 9v3.75m9-.75a9 9 0 11-18 0 9 9 0 0118 0zm-9 3.75h.008v.008H12v-.008z"></path>
            </svg>
            <h2 Id="ISCF"></h2>
          </div>
        </div>
      </div>

      <!-- IEM -->
      <div class="w-full flex flex-col gap-y-3 border-2 rounded border-black px-3 py-1 shadow-lg">
        <h1 class="text-center text-2xl font-bold">Ingeniería Electromecánica</h1>
        <div class="w-full flex flex-col gap-y-1">
          <div class="w-full flex flex-row gap-x-1 items-center">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
              stroke="currentColor" class="w-12 h-12">
              <path stroke-linecap="round" stroke-linejoin="round"
                d="M11.35 3.836c-.065.21-.1.433-.1.664 0 .414.336.75.75.75h4.5a.75.75 0 00.75-.75 2.25 2.25 0 00-.1-.664m-5.8 0A2.251 2.251 0 0113.5 2.25H15c1.012 0 1.867.668 2.15 1.586m-5.8 0c-.376.023-.75.05-1.124.08C9.095 4.01 8.25 4.973 8.25 6.108V8.25m8.9-4.414c.376.023.75.05 1.124.08 1.131.094 1.976 1.057 1.976 2.192V16.5A2.25 2.25 0 0118 18.75h-2.25m-7.5-10.5H4.875c-.621 0-1.125.504-1.125 1.125v11.25c0 .621.504 1.125 1.125 1.125h9.75c.621 0 1.125-.504 1.125-1.125V18.75m-7.5-10.5h6.375c.621 0 1.125.504 1.125 1.125v9.375m-8.25-3l1.5 1.5 3-3.75">
              </path>
            </svg>
            <h2 id="IEML"></h2>
          </div>

          <div class="w-full flex flex-row gap-x-1 items-center">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
              stroke="currentColor" class="w-12 h-12">
              <path stroke-linecap="round" stroke-linejoin="round"
                d="M12 9v3.75m9-.75a9 9 0 11-18 0 9 9 0 0118 0zm-9 3.75h.008v.008H12v-.008z"></path>
            </svg>
            <h2 id="IEMF"></h2>
          </div>
        </div>
      </div>
    </div>

    <div class="flex flex-col w-1/3 pt-20">
      <!-- IER -->
      <div class="w-full flex flex-col gap-y-3 border-2 rounded border-black px-3 py-1 shadow-lg">
        <h1 class="text-center text-2xl font-bold">Ingeniería renovables</h1>
        <div class="w-full flex flex-col gap-y-1">
          <div class="w-full flex flex-row gap-x-1 items-center">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
              stroke="currentColor" class="w-12 h-12">
              <path stroke-linecap="round" stroke-linejoin="round"
                d="M11.35 3.836c-.065.21-.1.433-.1.664 0 .414.336.75.75.75h4.5a.75.75 0 00.75-.75 2.25 2.25 0 00-.1-.664m-5.8 0A2.251 2.251 0 0113.5 2.25H15c1.012 0 1.867.668 2.15 1.586m-5.8 0c-.376.023-.75.05-1.124.08C9.095 4.01 8.25 4.973 8.25 6.108V8.25m8.9-4.414c.376.023.75.05 1.124.08 1.131.094 1.976 1.057 1.976 2.192V16.5A2.25 2.25 0 0118 18.75h-2.25m-7.5-10.5H4.875c-.621 0-1.125.504-1.125 1.125v11.25c0 .621.504 1.125 1.125 1.125h9.75c.621 0 1.125-.504 1.125-1.125V18.75m-7.5-10.5h6.375c.621 0 1.125.504 1.125 1.125v9.375m-8.25-3l1.5 1.5 3-3.75">
              </path>
            </svg>
            <h2 Id="IERL"></h2>
          </div>

          <div class="w-full flex flex-row gap-x-1 items-center">
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5"
              stroke="currentColor" class="w-12 h-12">
              <path stroke-linecap="round" stroke-linejoin="round"
                d="M12 9v3.75m9-.75a9 9 0 11-18 0 9 9 0 0118 0zm-9 3.75h.008v.008H12v-.008z"></path>
            </svg>
            <h2 Id="IERF"></h2>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>

.progress-bar {
    height: 20px;
    background-color: #f1f1f1;
    border-radius: 5px;
    overflow: hidden;
  }

  .progress {
    height: 100%;
    width: 0;
    background-color: #4caf50;
    transition: width 0.5s ease;
  }

.fond{
  background-color: rgb(135,206,250);
}

.fonddown{
  background-color:rgb(135,206,250);
}
.title{
  font-size: 25px;
}
.text{
  font-size: 20px;
}
.bolded {
 font-weight: bold; 
 font-size: 20px;
 text-decoration: underline;
}

.bolded2 {
 font-weight: bold; 
 font-size: 20px;
}


header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-center;
    flex-wrap: wrap;
  }

  nav {
    text-align: center;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>