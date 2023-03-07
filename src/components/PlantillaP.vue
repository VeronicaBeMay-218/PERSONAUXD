


<script>


    import axios from 'axios'
import BntEnviar from './bntEnviar.vue';
import inputF from './inputF.vue';
import inputEdad from './inputEdad.vue';
import selectCivil from './selectCivil.vue';
import inputNor from './inputNor.vue';
import sliderPe from './sliderPe.vue';
import inputSlider from './inputSlider.vue';

inputSlider

    export default {
    data() {
        return {
            nombre: "",
            edad: "",
            estadoCivil: "",
            trabajo: "",
            residencia: "",
            cita: "",
            citaAutor: "",
            bio: "",
            personalidad01: "",
            personalidad02: "",
            personalidad03: "",
            personalidad04: "",
            
            objetivos: [],
            frustraciones: [],
            motivaciones: [],
            marcas: "",
        };
    },
    methods: {
        agregarUsuario() {
            axios
                .post("/api/guardarPersonasUxd.php", {
                nombre: this.nombre,
                edad: this.edad,
                estadoCivil: this.estadoCivil,
                trabajo: this.trabajo,
                residencia: this.residencia,
                cita: this.cita,
                citaAutor: this.citaAutor,
                bio: this.bio,
                personalidad01: this.personalidad01,
                personalidad02: this.personalidad02,
                personalidad03: this.personalidad03,
                personalidad04: this.personalidad04,
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

    

    
    components: { BntEnviar , inputF, inputEdad, selectCivil, inputNor, inputSlider}
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
      <inputNor v-model="trabajo"/>
    </div>


    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Residencia
      </label>
      <inputNor v-model="residencia"/>
    </div>
  </div>

  <div class="flex flex-nowrap">
    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Cita
      </label>
      <inputNor v-model="cita"/>
    </div>
   
    <div class="w-full md:w-1/2 px-">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-last-name">
        Cita Autor
      </label>
      <inputNor v-model="citaAutor"/>
    </div>
    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Bio
      </label>
      <inputNor v-model="bio"/>
    </div>

  </div>


  <div class="flex flex-nowrap">
    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Personalidad01
      </label>
      <inputSlider v-model="personalidad01"/>
    </div>
   
    <div class="w-full md:w-1/2 px-">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-last-name">
        Personalidad02
      </label>
      <inputSlider v-model="personalidad02"/>
    </div>
    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Personalidad03
      </label>
      <inputSlider v-model="personalidad03"/>
    </div>

    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Personalidad04
      </label>
      <inputSlider v-model="personalidad04"/>
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


    
    