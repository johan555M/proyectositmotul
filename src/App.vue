<script setup>

import Api from './components/Api.vue'
import Eval from './components/Eval.vue'
import EvalIng from './components/EvalIng.vue'
import Datos from './components/Datos.vue'
</script>


<template>
  <header>
    <Api> </Api>
  </header>
  <body>
    <Eval></Eval>

    <div class="espacio"></div>
      <Datos></Datos>
      
    <div class="espacio"></div>
    <EvalIng></EvalIng>

    <div class="espacio"></div>

   
  </body>


</template>

<style>
  /* Estilo para agregar espacio hacia abajo */
  .espacio {
     /* Ajusta el valor según tus necesidades */
    background-color: rgb(135,206,250); /* Cambia el color según tus preferencias */
    height: 40px; 
  }

 
</style>

