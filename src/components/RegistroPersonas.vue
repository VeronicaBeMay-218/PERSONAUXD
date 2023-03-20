<script>
//importación de componentes
import BotonEnviar from '../components/BotonEnviar.vue';
import InputT from './InputT.vue';
import TextA from './TextA.vue';
import InputSlider from '../components/InputSlider.vue';
import InputArray from '../components/InputTextArray.vue';
//import InputArray2 from '../components/InputTextArray2.vue';

import axios from 'axios';



export default {
  components:{
    //nombre con el que se llama a los componentes
    BotonEnviar, InputT, TextA, InputSlider, InputArray, //InputArray2
  },
  
  emits: ['dataIT, dataTA, porcentaje, dataA'],

    data() {
      return {
        //variables
        Nombre: "",
        Edad: "",
        EstadoCivil: "",
        Trabajo: "",
        Residencia: "",
        Cita: "",
        CitaAutor: "",
        Bio: "",
        Personalidad1: "50",
        Personalidad2: "50",
        Personalidad3: "50",
        Personalidad4: "50",

        NuevoObje: "",
        ArrayObjetivos: [{value:''}],
        
        NuevoFrus: "",
        ArrayFrustraciones: [{value:''}],

        NuevoMot: "",
        NuevoPorcMot: "0",
        Motivaciones: "",

        Marcas: "",

        //variable validaciones
        validar:false
      };
    },
    mounted() {
    },
    methods: {

        //Funciones para pasar los datos que recibe como componentes a las variables declaradas
        
        //Nombre
        DataIT1(t){
          //le asignamos lo que recibe a la variable
          this.Nombre=t
        },

        //Edad
        DataIT2(t){
          //le asignamos lo que recibe a la variable
          this.Edad=t
        },

        //Trabajo
        DataIT3(t){
          //le asignamos lo que recibe a la variable
          this.Trabajo=t
        },

        //Residencia
        DataIT4(t){
          //le asignamos lo que recibe a la variable
          this.Residencia=t
        },

        //Cita
        TextAreaC(a){
          //le asignamos lo que recibe a la variable
          this.Cita=a
        },

        //Biografia
        TextAreaB(a){
          //le asignamos lo que recibe a la variable
          this.Bio=a
        },

        //Personalidades
        SliderP1(s){
          this.Personalidad1=s
        },

        SliderP2(s){
          this.Personalidad2=s
        },

        SliderP3(s){
          this.Personalidad3=s
        },

        SliderP4(s){
          this.Personalidad4=s
        },

        //Objetivos
        Objetivoos(s, index){
          this.ArrayObjetivos[index] = {value: s}
          
        },
        //Frustraciones
        Frustracionees(s, index){
          this.ArrayFrustraciones[index] = {value: s}
          
        }, 
        //Motivaciones
        Motivacionees(s, po , index){
          this.ArrayMotivaciones[index] = {value: s,porcent: po }
          //console.log(this.ArrayMotivaciones)
        },

        //Función para enviar informacion de una persona
        Registrar() {
          if(this.Validar()){
            axios
              .post("/api/guardarPersonasUxd.php", {
              //declaracion de variables del backend
              nombre: this.Nombre,
              edad: this.Edad,
              estadoCivil: this.EstadoCivil,
              trabajo: this.Trabajo,
              residencia: this.Residencia,
              cita: this.Cita,
              citaAutor: this.CitaAutor,
              bio: this.Bio,
              personalidad01: this.Personalidad1,
              personalidad02: this.Personalidad2,
              personalidad03: this.Personalidad3,
              personalidad04: this.Personalidad4,
              objetivos: this.ArrayObjetivos,
              frustraciones: this.ArrayFrustraciones,
              motivaciones: this.Motivaciones,
              marcas: this.Marcas
            })
            .then((response) => {
            //comprobación de envio a la base de datos con numero 200
            console.log(response.status);
            });
          }
            
        },

        Validar(){
          //nombre
          if(this.Nombre != "" && !isNaN (this.Nombre) === false && this.Nombre.length <201 && this.Nombre.length > 2 ) {
            console.log("Nombre correcto")
             
            //edad
            if (this.Edad.length < 3 && this.Edad != ""){
              console.log("Edad correcto")
            }else{
              console.log("Escribe edad")
            }

            //Estado civil
            if (this.EstadoCivil != ""){
              console.log("Estado civil correcto")
            }else{
              console.log("Selecciona estado civil")
              return false
            }

            //Trabajo
            if (this.Trabajo.length < 201 && this.Trabajo != "" && !isNaN (this.Trabajo) === false){
              console.log("Trabajo correcto")
            }else{
              console.log("Escribe un trabajo")
              return false
            }

            //Residencia
            if (this.Residencia.length < 201 && this.Residencia != "" && !isNaN (this.Residencia) === false){
              console.log("Residencia correcta")
            }else{
              console.log("Escribe una residencia")
              return false
            }

            //Cita
            if (this.Cita.length < 501 && this.Cita != "" && !isNaN (this.Cita) === false){
              console.log("Cita correcta")
            }else{
              console.log("Escribe una cita")
              return false
            }

            //CitaAutor
            if (this.CitaAutor.length < 501 && this.CitaAutor != "" && !isNaN (this.CitaAutor) === false){
              console.log("CitaAutor existe")
            }else{
              console.log("Escribe una CitaAutor")
              return false
            }

            //Bio
            if (this.Bio.length < 701 && this.Bio != ""){
              console.log("Bio correcta")
            }else{
              console.log("Bio incorrecta")
              return false
            }

          return true
                       
          }
          else{
            console.log("No se pudo registrar")
            return false
          }
          
        }
    },
    
}


</script>

<template class="flex mx-auto">




<div class="w-full  flex justify-item-center">

    
    <div class="w-4/5 m-w-450 m-auto h-auto rounded-lg bg-white py-8 px-7 mb-2">
      
    <!-- component card -->
    <div class=" bg-[#475569] rounded overflow-hidden shadow-lg">

<form class="w-full mt-6 ">
        
        <div class="grid grid-cols-2  ">

          <!-- component -->

   
    <body>
      <div class="flex justify-center items-center">
            <div class=" bg-[#d6d3d1] relative flex flex-col items-center  rounded-[20px] w-[700px] max-w-[95%] max-w-[95%] mx-auto bg-white bg-clip-border shadow-3xl shadow-shadow-500 dark:!bg-navy-800 dark:text-white dark:!shadow-none p-1">
                <div class="mt-2 mb-8 w-full">
                    <div class="relative w-full">

                      <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" width="440" height="173" viewBox="0 0 179 173" fill="none">
<rect width="179" height="173" fill="url(#pattern0)"/>
<defs>
<pattern id="pattern0" patternContentUnits="objectBoundingBox" width="1" height="1">
<use xlink:href="#image0_106_2" transform="matrix(0.00306748 0 0 0.00317387 0 -0.00940636)"/>
</pattern>
<image id="image0_106_2" width="326" height="321" xlink:href="data:image/jpeg;base64,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"/>
</defs>
</svg>
                      
                    </div>
                    <div class="mb-3 flex items-center justify-between px-1 md:items-start">
                      <div class="w-full">
              
              
              <!-- Nombre -->
              <label class="block text-black font-bold md:text-left my-2 md:mb-0">
                Nombre:
              </label>
              
              <!--Uso al componente-->
              <InputT @dataIT="DataIT1" > </InputT>
          
            </div>
          </div>


          <div class="mb-3 flex items-center justify-between px-1 md:items-start">
            <div class="w-full mt-4">
              <label class="block text-black font-bold md:text-left my-2 md:mb-0" >
                Edad:
              </label>
              
              <!--Uso al componente-->
              <InputT @dataIT= "DataIT2" > </InputT>

            </div>
          </div>

          <div class="mb-3 flex items-center justify-between px-1 md:items-start">
                      <!-- Estado Civil -->
            <div class="w-full mt-4">
              <label class="block text-black font-bold md:text-left my-2 md:mb-0">
                Estado Civil:
              </label>
              <select v-model="EstadoCivil" name="EstadoCivil" id="EstadoCivil"  class="w-full my-2 py-2.5 px-4 rounded-lg bg-gray-50 focus:shadow focus:bg-white focus:outline-none">
                <option disabled value="">Selecciona </option>
                <option value="1">Soltero</option>
                <option value="2">Casado </option>
                <option value="3">Divorciado</option>
                <option value="4">Separado</option>
                <option value="5">Unión libre</option>
                <option value="6">Viudo</option>
              </select>
            </div>
          </div>


          <div class="mb-3 flex items-center justify-between px-1 md:items-start">
                      <!-- Trabajo -->
            <div class="w-full mt-4">
              <label class="block text-black font-bold md:text-left my-2 md:mb-0">
                Trabajo:
              </label>
              
              <!--Uso al componente-->
              <InputT @dataIT= "DataIT3" > </InputT>
            </div>
          </div>


          <div class="mb-3 flex items-center justify-between px-1 md:items-start">
                       <!-- Residencia -->
            <div class="w-full mt-4">
              <label class="block text-black font-bold md:text-left my-2 md:mb-0">
                Residencia:
              </label>
              
              <!--Uso al componente-->
              <InputT @dataIT= "DataIT4"> </InputT>

            </div>
          </div>


          <div class="mb-3 flex items-center justify-between px-1 md:items-start">
                       <!-- Cita -->
            <div class="w-full mt-4">
              <label class="block text-black font-bold md:text-left my-2 md:mb-0">
                Escribe una cita:
              </label>
              
              <!--Uso al componente-->
              <TextA @dataTA = "TextAreaC"></TextA>
            </div>

            <!-- Autor -->
            <div class="w-full mt-4">
              <label class="block text-black font-bold md:text-left my-2 md:mb-0">
               Autor de la cita:
              </label>
              <input type="text" v-model="CitaAutor" class="w-full py-2.5 px-4 rounded-lg bg-gray-50 focus:shadow focus:bg-white focus:outline-none" id="CitaAutor" placeholder=""/>
            </div>
          </div>


          <div class="mb-3 flex items-center justify-between px-1 md:items-start">
            <div class="w-full mt-4">


              <label class="block text-black font-bold md:text-left my-2 md:mb-0">
                Motivaciones  
              </label>
              <input type="text" v-model="Motivaciones" class="w-full py-2.5 px-4 rounded-lg bg-gray-100 focus:shadow focus:bg-white focus:outline-none" id="Motivaciones" placeholder="Separa por comas"/>
            </div>
            
            <div class="w-full mt-4">

              <label class="block text-black font-bold md:text-left my-2 md:mb-0">
                Marcas  
              </label>
              <input type="text" v-model="Marcas" class="w-full py-2.5 px-4 rounded-lg bg-gray-100 focus:shadow focus:bg-white focus:outline-none" id="Marcas" placeholder="Separa por comas"/>


            </div>
          </div>


                    <div class="flex items-center justify-between md:items-center lg:justify-between ">
                        
                       </div>
                </div>
            </div>
            </div>
    </body>
          
          <!-- Personalidades  -->
          <div class=" p-3 rounded-lg w-full ">

            <!-- component -->

   
    <body >
        <div class="flex flex-col justify-center items-center">
            <div class="bg-[#d6d3d1] relative flex flex-col items-center rounded-[20px] w-[700px] max-w-[100%] mx-auto bg-white bg-clip-border shadow-3xl shadow-shadow-500 dark:!bg-navy-800 dark:text-white dark:!shadow-none p-1">
                <div class="mt-2 mb-8 w-full">

                    <p class="mt-2 px-2 text-base text-gray-600">
                   <!-- Biografia -->
            <div class="w-full mt-4">
              <label class="block text-black font-bold md:text-left my-2 md:mb-0">
                Biografía
              </label>
              
              <!--Uso al componente-->
              <TextA @dataTA = "TextAreaB"></TextA>

            </div>
                    </p>



                </div> 





                <div class="grid grid-cols-2 gap-4 px-2 w-full">


                  <div class="flex flex-col justify-center rounded-2xl bg-white bg-clip-border px-3 py-4 shadow-3xl shadow-shadow-500 dark:!bg-navy-700 dark:shadow-none">
                    <p class=" text-gray-600">Personalidades</p>
                    <p class="text-base font-medium text-navy-700 dark:text-white">
                      <div class="w-full mt-4">
              

              <div class="flex justify-between px-3  ">
                <label class="text-black text-left md:text-left my-2 md:mb-0">
                 Extrovertido: <br>  {{ this.Personalidad1 }}%
                </label>
                
                <label class="text-black text-end  mr-0 md:text-right my-2 md:mb-0">
                  Introvertido: <br> {{ 100 - this.Personalidad1 }}%
                </label>

              </div>

              <!--Uso al componente-->
              <InputSlider @porcentaje="SliderP1" ></InputSlider>
              
            </div>
            
            <div class="w-full mt-4">
              

              <div class="flex justify-between px-3  ">
                <label class="text-black text-left md:text-left my-2 md:mb-0">
                  Organizado: <br>  {{ this.Personalidad2 }}%
                </label>
                
                <label class="text-black text-end  mr-0 md:text-right my-2 md:mb-0">
                  Desordenado: <br> {{ 100 - this.Personalidad2 }}%
                </label>

              </div>

              <!--Uso al componente-->
              <InputSlider @porcentaje="SliderP2" ></InputSlider>
            </div>
                    </p>
                    </div>

                    <div class="flex flex-col justify-center rounded-2xl bg-white bg-clip-border px-3 py-4 shadow-3xl shadow-shadow-500 dark:!bg-navy-700 dark:shadow-none">
                    <p class=" text-gray-600">Personalidades</p>
                    <p class="text-base font-medium text-navy-700 dark:text-white">
                      <div class="w-full">
              

              <div class="flex justify-between px-3  ">
                <label class="text-black text-left md:text-left my-2 md:mb-0">
                 Creativo: <br>  {{ this.Personalidad3 }}%
                </label>
                
                <label class="text-black text-end  mr-0 md:text-right my-2 md:mb-0">
                  Analítico: <br> {{ 100 - this.Personalidad3 }}%
                </label>

              </div>

              <!--Uso al componente-->
              <InputSlider @porcentaje="SliderP3" ></InputSlider>
              
            </div>
            
            <div class="w-full mt-4">
              

              <div class="flex justify-between px-3  ">
                <label class="text-black text-left md:text-left my-2 md:mb-0">
                  Rico en tiempo: <br>  {{ this.Personalidad4 }}%
                </label>
                
                <label class="text-black text-end  mr-0 md:text-right my-2 md:mb-0">
                  Ocupado: <br> {{ 100 - this.Personalidad4 }}%
                </label>

              </div>

              <!--Uso al componente-->
              <InputSlider @porcentaje="SliderP4" ></InputSlider>
            </div>
                    </p>
                    </div>

                    <div class="flex flex-col items-start justify-center rounded-2xl bg-white bg-clip-border px-3 py-4 shadow-3xl shadow-shadow-500 dark:!bg-navy-700 dark:shadow-none">
                    
                    <p class="text-base font-medium text-navy-700 dark:text-white">
                        <!-- Objetivos -->
            <div class=" ">
              <label class="block text-black font-bold md:text-left my-2 md:mb-0">
                Objetivos
              </label>
              <div v-for="(obj, index) in ArrayObjetivos">
                <InputArray @dataA="Objetivoos" :index="index"> </InputArray>
              </div>
              <BotonEnviar v-on:click.prevent="this.ArrayObjetivos.push(NuevoObje)"> Agregar </BotonEnviar>
            </div>
                    </p>
                    </div>

                    <div class="flex flex-col rounded-2xl bg-white bg-clip-border px-3 py-4 shadow-3xl shadow-shadow-500 dark:!bg-navy-700 dark:shadow-none">
                    
                    
<!-- Frustraciones  --> 
<div class=" ">
              <label class="block text-black font-bold md:text-left my-2 md:mb-0">
                Frustraciones   
              </label>
              <div v-for="(frus, index) in ArrayFrustraciones">
                <InputArray @dataA="Frustracionees" :index="index"> </InputArray>
              </div>
              <BotonEnviar v-on:click.prevent="this.ArrayFrustraciones.push(NuevoFrus)"> Agregar </BotonEnviar>
            </div>
            


                    </div>

                   
                </div>
            </div>  
            </div>
    </body>

          </div>
          
        </div>

        <!--Boton Registrar-->
                        
        <BotonEnviar @click="Registrar()" >
              Enviar
            </BotonEnviar>

      </form>   
    </div>


      
    </div>
    
  </div>  
  
</template>