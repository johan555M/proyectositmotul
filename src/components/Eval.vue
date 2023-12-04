<script setup>

import { onMounted } from 'vue';
import { ref } from 'vue';
import  { computed } from 'vue';
import dayjs from 'dayjs';
import 'dayjs/locale/es'; // Importa el idioma español

dayjs.locale('es');

const info = ref('');

async function fetchData() {
  try {
    const response = await fetch('https://sitmotul.com.mx/api/statusEval')
    const data = await response.json();
    info.value = data
    // isLoading.value = false
    console.log(info.value);
    // document.getElementById('per').textContent = info.value['periodo'];
  } catch (error) {
    console.error('Error al obtener datos:', error);
  }
}
onMounted(() => {
  fetchData();
})
const fechain = computed(() => {
    return dayjs(info.value.inicio).format('dddd, DD [de] MMMM [del] YYYY');
});

const fechafi = computed(() => {
    return dayjs(info.value.fin).format('dddd, DD [de] MMMM [del] YYYY');
});
</script>

<template>
   <body class="fonddown text bolded2">
    
    <main>
      <div class="w-full flex flex-row px-60 gap-x-5 pt-20">
        <div class="w-1/2 flex flex-col gap-y-3 place-items-center ">
          <svg xmlns="http://www.w3.org/2000/svg" width="70" height="70" fill="#000000" viewBox="0 0 256 256"><path d="M208,32H184V24a8,8,0,0,0-16,0v8H88V24a8,8,0,0,0-16,0v8H48A16,16,0,0,0,32,48V208a16,16,0,0,0,16,16H208a16,16,0,0,0,16-16V48A16,16,0,0,0,208,32ZM72,48v8a8,8,0,0,0,16,0V48h80v8a8,8,0,0,0,16,0V48h24V80H48V48ZM208,208H48V96H208V208Z"></path></svg>
          <div class=" w-full flex flex-col gap-y-1 place-items-center">
            <h1>Fecha de inicio:</h1>
            <h2>{{fechain}}</h2>
          </div>

        </div>


        <div class="w-1/2 flex flex-col gap-y-3 place-items-center ">
          <svg xmlns="http://www.w3.org/2000/svg" width="70" height="70" fill="#000000" viewBox="0 0 256 256"><path d="M208,32H184V24a8,8,0,0,0-16,0v8H88V24a8,8,0,0,0-16,0v8H48A16,16,0,0,0,32,48V208a16,16,0,0,0,16,16H208a16,16,0,0,0,16-16V48A16,16,0,0,0,208,32ZM72,48v8a8,8,0,0,0,16,0V48h80v8a8,8,0,0,0,16,0V48h24V80H48V48ZM208,208H48V96H208V208Zm-38.34-85.66a8,8,0,0,1,0,11.32l-48,48a8,8,0,0,1-11.32,0l-24-24a8,8,0,0,1,11.32-11.32L116,164.69l42.34-42.35A8,8,0,0,1,169.66,122.34Z"></path></svg>
          <div class=" w-full flex flex-col gap-y-1 place-items-center ">
            <h1>Fecha de finalización:</h1>
            <h2>{{fechafi}}</h2>
          </div>

        </div>
      </div>
    </main>
  </body>
</template>

<script>
export default {
  name: 'PhStudentLight'
}
</script>






<style scoped>

.fond{
  background-color: rgb(0,191,255);
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