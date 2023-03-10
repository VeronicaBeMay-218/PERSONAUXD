


<script>


    import axios from 'axios'
import BntEnviar from './bntEnviar.vue';
import inputF from './inputF.vue';
import inputEdad from './inputEdad.vue';
import selectCivil from './selectCivil.vue';
import inputNor from './inputNor.vue';
import sliderPe from './sliderPe.vue';
import inputSlider from './inputSlider.vue';
import btnSubmit from './btnSubmit.vue';

inputSlider

    export default {
    data() {
        return {
            nombre: "",
            edad: "",
         
        };
    },
    methods: {
        agregarUsuario() {
            axios
                .post("/api/guardarPersonasUxd.php", {
                nombre: this.nombre,
                edad: this.edad,
                
                //completar las variables, estas deben llamarse como las que se recibirán en el backend sin el símbolo del dolar $
            })
                .then((response) => {
                console.log(response.status);
            });
        },
    },

    

    
    components: { BntEnviar , inputF, inputEdad, selectCivil, inputNor, inputSlider, btnSubmit}
}
    </script>
    
  






<template>



  <div class="flex items-center font-bold ... w-120 rounded overflow-hidden shadow-lg p-12 m-10 snap-start bg-[#fbcfe8]">

   
  <div>
    
</div>

  <div>
  
    
     
  <div class="flex flex-nowrap">


    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Nombre
      </label>

    <div>
      <inputF/>
    </div>
   
       

    </div>

    <div class="w-full md:w-1/2 px-">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-last-name">
        Edad
      </label>
      <inputEdad/>
      
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
      <inputNor/>
    </div>


    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Residencia
      </label>
      <inputNor/>
    </div>
  </div>

  <div class="flex flex-nowrap">
    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Cita
      </label>
      <inputNor/>
    </div>
   
    <div class="w-full md:w-1/2 px-">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-last-name">
        Cita Autor
      </label>
      <inputNor/>
    </div>
    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Bio
      </label>
      <inputNor/>
    </div>

  </div>


  <div class="flex flex-nowrap">
    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Personalidad01
      </label>
      <inputSlider/>
    </div>
   
    <div class="w-full md:w-1/2 px-">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-last-name">
        Personalidad02
      </label>
      <inputSlider/>
    </div>
    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Personalidad03
      </label>
      <inputSlider/>
    </div>

    <div class="w-full md:w-1/2 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
        Personalidad04
      </label>
      <inputSlider/>
    </div>

  </div>




  <div class="flex flex-wrap -mx-3 mb-2">
    <div class="w-full md:w-1/3 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-city">
        Objetivos
      </label>
      <inputNor/>
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
    </div>

    <div class="w-full md:w-1/3 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-city">
        Frustraciones
      </label>
      <inputNor/>
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
    </div>
   
    <div class="w-full md:w-1/3 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-zip">
       Motivaciones
      </label>
      <inputNor/>
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
      
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-zip">
       porcentaje
      </label>
      <inputNor/>
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
    
    </div>
  </div>


  <div class="flex flex-wrap -mx-3 mb-2">
    <div class="w-full md:w-1/3 px-3 mb-6 md:mb-0">
      <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-city">
        Marcas
      </label>
      <inputNor/>
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
    </div>
    
  </div>

<div>
 <btnSubmit  @click="agregarUsuario()"/>
</div>

 <div>

 </div>

  </div>
</div>
</template>


    
    