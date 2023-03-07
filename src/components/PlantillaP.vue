


<script>


    import axios from 'axios'
import BntEnviar from './bntEnviar.vue';
import inputF from './inputF.vue';
import inputEdad from './inputEdad.vue';
import selectCivil from './selectCivil.vue';
    

    export default {
    data() {
        return {
            nombre: "",
            estado_civil: "",
            trabajo: "",
            personalidad: "",
            personalidades: [],
            marcas: "",
        };
    },
    methods: {
        agregarUsuario() {
            axios
                .post("/api/guardarPersonasUxd.php", {
                nombre: this.nombre,
                objetivos: this.objetivos,
                frustraciones: this.frustraciones,
                motivaciones: this.motivaciones,
                marcas: this.marcas,
                //completar las variables, estas deben llamarse como las que se recibirán en el backend sin el símbolo del dolar $
            })
                .then((response) => {
                console.log(response.status);
            });
        },
    },
    components: { BntEnviar , inputF, inputEdad, selectCivil}
}
    </script>
    
  






<template>



  <div class="flex items-center font-bold ... w-120 rounded overflow-hidden shadow-lg p-12 m-10 snap-start bg-[#fbcfe8]">

   
  <div>
    
</div>

  <div>
  
    <form class="">
     
  <div class="flex flex-nowrap">


    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Nombre
      </label>

    <div>
      <inputF  v-model="nombre"/>
    </div>
   
       

    </div>

    <div class="w-full md:w-1/2 px-">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-last-name">
        Edad
      </label>
      <inputEdad v-model="edad"/>
      
      </div>
    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Estado Civil
      </label>
      <selectCivil/>
      
    </div>

    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Trabajo
      </label>
      <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white"  id="trabajo" type="text" v-model="trabajo">
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
    </div>


    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Residencia
      </label>
      <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" id="residencia" type="text" v-model="residencia">
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
    </div>
  </div>

  <div class="flex flex-nowrap">
    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Cita
      </label>
      <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" id="cita" type="text" v-model="cita">
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
    </div>
   
    <div class="w-full md:w-1/2 px-">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-last-name">
        Cita Autor
      </label>
      <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" id="citaAutor" type="text" v-model="citaAutor">
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
    </div>
    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Bio
      </label>
      <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" id="bio" type="text" v-model="bio">
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
    </div>

  </div>


  <div class="flex flex-nowrap">
    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Personalidad01
      </label>
      <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" id="personalida01" type="text" v-model="personalida01">
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
    </div>
   
    <div class="w-full md:w-1/2 px-">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-last-name">
        Personalidad02
      </label>
      <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" id="personalida02" type="text" v-model="personalida02">
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
    </div>
    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Personalidad03
      </label>
      <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" id="personalida03" type="text" v-model="personalida03">
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
    </div>

    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Personalidad04
      </label>
      <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" id="personalida04" type="text" v-model="personalida04">
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
    </div>

  </div>




  <div class="flex flex-wrap -mx-3 mb-2">
    <div class="w-full md:w-1/3 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-city">
        Objetivos
      </label>
      <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" id="objetivos" type="text" v-model="objetivos">
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
    </div>

    <div class="w-full md:w-1/3 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-city">
        Frustraciones
      </label>
      <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" id="frustraciones" type="text" v-model="frustraciones">
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
    </div>
   
    <div class="w-full md:w-1/3 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-zip">
       Motivaciones
      </label>
      <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" type="text" v-model="motivaciones">
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
      
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-zip">
       porcentaje
      </label>
      <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" id="porcentaje" type="text" v-model="porcentaje">
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
    
    </div>
  </div>


  <div class="flex flex-wrap -mx-3 mb-2">
    <div class="w-full md:w-1/3 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-city">
        Marcas
      </label>
      <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" id="marcas" type="text" v-model="marcas">
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
    </div>
    
  </div>

<div  @click="agregarUsuario">
 <BntEnviar/>
</div>

 <div>

 </div>
</form>
  </div>
</div>
</template>


    
    