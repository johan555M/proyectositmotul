<script setup>


import { onMounted } from 'vue';
import { ref } from 'vue';



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



</script>




<template>
  <body class="fond">
    <header class="w-full">
      <div class="w-full flex flex-col gap-y-3">
        <div class="w-full flex flex-col gap-y-1 place-items-center px-60">
          <img alt="Sit logo" class="logo" src="@/components/icons/logoS.svg" width="200" height="200" />
          <h1 class="title">SITMOTUL</h1>
          <h3 class="text">Información sobre la evaluación al tutor del ciclo escolar {{ info.periodo }}</h3>
        </div>
        
        
        
      </div>

    </header>
  </body>
  
</template>



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