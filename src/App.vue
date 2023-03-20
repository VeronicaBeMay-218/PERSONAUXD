<script setup>
import { RouterLink, RouterView } from 'vue-router'
import Titulo from "./components/Titulo.vue";
</script>

<template class="flex-col justify-center w-full h-full p-2">

<div class="w-full h-full  from-purple-600 justify-items-center">
      
      <header>
  

        <nav class="p-5 shadow md:flex md:items-center md:justify-between">
      <div class="flex justify-between items-center">
      
       
      </div>
  
      <ul class="md:flex md:items-center z-[-1] md:z-auto md:static absolute w-full left-0 md:w-auto md:py-0 py-4 md:pl-0 pl-7 md:opacity-100 opacity-0 top-[-400px] transition-all ease-in duration-500">
        <li class="mx-4 my-6 md:my-0">
          <RouterLink to="/">Inicio</RouterLink>
          </li>
        <li class="mx-4 my-6 md:my-0">
          <RouterLink to="/RegistroPersonas">Registro</RouterLink>
         </li>
        <li class="mx-4 my-6 md:my-0">
          <RouterLink to="/ListaPersonas">Personas</RouterLink>
          </li>

  
  
      </ul>
    </nav>
        
        
        <div class="w-full">
  
          <Titulo msg="Personas UX" />
  
        </div>
  
      </header>
  
  
    <RouterView />
  </div>
  </template>