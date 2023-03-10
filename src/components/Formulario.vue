
<script>
    import axios from 'axios'


    export default {
      data(){
        return {
          nombre: '',
          edad: 0,
          estado_civil: '',
          trabajo: '',
          personalidad: '',
          personalidades: [],
          
        }
      },
      
      methods: {
        agregarUsuario()
        {
          axios
.post("/api/guardarPersonasUxd.php", {
nombre: this.nombre,
objetivos:this.objetivos,
frustraciones: this.frustraciones,
motivaciones: this.motivaciones,
marcas: this.marcas,
//completar las variables, estas deben llamarse como las que se recibirán en el backend sin el símbolo del dolar $
})
.then((response) => {
console.log(response.status)
});

        },
        
      }
    }
    </script>
    
  




<template>
    
    <div class="flex items-center font-bold ... w-120 rounded overflow-hidden shadow-lg p-12 m-10 snap-start bg-[#fbcfe8]">
      <div class="row">
        <div class="col m12 card-panel">
    
          
              <div class="row">
                <div class="block text-gray-700 text-sm font-bold mb-2" for="username">
                  <label class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2" for="grid-first-name">
                  
                  Nombre</label>
                  <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" id="nombre" type="text" v-model="nombre" placeholder="Veronica">
      <p class="text-red-500 text-xs italic">Por favor rellene este campo.</p>
                  
                </div>
                
              </div>
    
            <div class="row">
              <div class="block text-gray-700 text-sm font-bold mb-2" for="username">
                <label>Edad</label>
                <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="edad" type="number" v-model="edad">
              </div>

           
              <div class="block text-gray-700 text-sm font-bold mb-2" for="username">
                <label>Estado civil</label>
              <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="estadoCivil" type="text" v-model="estadoCivil">
              </div>
              <div class="block text-gray-700 text-sm font-bold mb-2" for="username">
                <label>Trabajo</label>
              <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="trabajo" type="text" v-model="trabajo">
              </div>
              <div class="block text-gray-700 text-sm font-bold mb-2" for="username">
                <label>Residencia</label>
              <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="residencia" type="text" v-model="residencia">
              </div>
              <div class="block text-gray-700 text-sm font-bold mb-2" for="username">
                <label>Cita</label>
              <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="cita" type="text" v-model="cita">
              </div>
              <div class="block text-gray-700 text-sm font-bold mb-2" for="username">
                <label>Cita Autor</label>
              <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="citaAutor" type="text" v-model="citaAutor">
              </div>
              <div class="block text-gray-700 text-sm font-bold mb-2" for="username">
                <label>bio</label>
              <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="bio" type="text" v-model="bio">
              </div>
            </div>
            
            <div class="block text-gray-700 text-sm font-bold mb-2" for="usernames">
              <div class="block text-gray-700 text-sm font-bold mb-2" for="username">
                <label>Personalidad 1</label>
              <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="personalida01" type="text" v-model="personalida01">
              </div>
              <div class="block text-gray-700 text-sm font-bold mb-2" for="username">
                <label>Personalidad 2</label>
              <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="personalida02" type="text" v-model="personalida02">
              </div>
              <div class="block text-gray-700 text-sm font-bold mb-2" for="username">
                <label>Personalidad 3</label>
              <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="personalida03" type="text" v-model="personalida03">
              </div>
              <div class="block text-gray-700 text-sm font-bold mb-2" for="username">
                <label>Personalidad 4</label>
              <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="personalida04" type="text" v-model="personalida04">
              </div>
            </div>

            <div class="block text-gray-700 text-sm font-bold mb-2" for="usernames">
          
                <div class="col m4 card-panel">
                  <label>Objetivos</label>
                  <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="objetivos" type="text" v-model="objetivo">
                  <br>
                  
                </div>
              
            </div>

            <div class="block text-gray-700 text-sm font-bold mb-2" for="usernames">
             
             <div class="col m4 card-panel">
               <label>Fustraciónes</label>
               <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="frustraciones" type="text" v-model="frustraciones">
               <br>
              
             </div>
          
         </div>


            <div class="block text-gray-700 text-sm font-bold mb-2" for="usernames">
              
                <div class="col m4 card-panel">
                
                  <label>Motivaciónes</label>
                  <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="motivaciones" type="text" v-model="motivaciones">
                  <div class="block text-gray-700 text-sm font-bold mb-2" for="username">
                <label>Porcentaje</label>
              <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="porcentaje" type="text" v-model="porcentaje">
              </div>
                 
                 
                  
                  
                </div>
              
            </div>

            

            <div class="block text-gray-700 text-sm font-bold mb-2" for="usernames">
             
                <div class="col m4 card-panel">
                  <label>Marcas</label>
                  <input class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" id="marcas" type="text" v-model="marcas">
                  
                  
                </div>
                
              
            </div>
            

           
    
            
    
            <div @click="agregarUsuario()">
              <button type="submit" class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline">AGREGAR<i class="material-icons right"></i></button>
            </div>
          
        </div>
      </div>
    
      
    </div>
    
    
    </template>
    

    
    