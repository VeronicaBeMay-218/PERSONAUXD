<script>
//importación de componentes
import BotonEnviar from '../components/BotonEnviar.vue';
import InputT from './InputT.vue';
import TextA from './TextA.vue';
import InputSlider from '../components/InputSlider.vue';
import InputArray from '../components/InputTextArray.vue';
import imgUsuario from '../components/imgUsuario.vue';
import InputSliderMot from '../components/InputSliderMot.vue';
import InputMot from '../components/InputMot.vue';


//import InputArray2 from '../components/InputTextArray2.vue';

import axios from 'axios';



export default {
  components:{
    //nombre con el que se llama a los componentes
    BotonEnviar, InputT, TextA, InputSlider, InputArray,InputSliderMot,InputMot, imgUsuario, //InputArray2
  },
  
  emits: ['dataIT, dataTA, porcentaje, dataA','valorInput'],

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

        Motivaciones: [],
            Motivaciones2: [],
            Motivaciones3: [],
            Motivaciones4: [],

        Marcas: "",
        ContadorFrustraciones: 1,
            ContadorMotivaciones: 1,
        DatoAgregarMotivacion: false,
        DatoAgregar2Motivacion: false,

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


        AgregarInput3(s){
                this.ContadorMotivaciones=this.ContadorMotivaciones+s
                if(this.ContadorMotivaciones==2){
                    this.DatoAgregarMotivacion=true
                }
                if(this.ContadorMotivaciones==3){
                    this.DatoAgregar2Motivacion=true
                }
            },
            AgregarMotivaciones(s){
                this.Motivaciones2=s
                this.Motivaciones={value: s,'porcentaje': this.ValMotivacion}
                console.log(this.Motivaciones)

            },
            AgregarMotivaciones2(s){
                this.Motivaciones3=s
                this.Motivaciones=[{value: this.Motivaciones2,'porcentaje': this.ValMotivacion},{value: this.Motivaciones3,'porcentaje':s}]
                console.log(this.Motivaciones3)

            },
            AgregarMotivaciones3(s){
                this.Motivaciones4=s
                this.Motivaciones=[{value: this.Motivaciones2},{value: this.Motivaciones3},{value: this.Motivaciones4}]

                console.log(this.Motivaciones4)
                console.log(this.Motivaciones)


            },

            ValorMotivacion(s){
                this.ValMotivacion=s;
                this.Motivaciones={value: this.Motivaciones2,'porcentaje':s}
                console.log(this.Motivaciones);
            },
            ValorMotivacion2(s){
                this.ValMotivacion2=s;
                this.Motivaciones=[{value: this.Motivaciones2,'porcentaje': this.ValMotivacion},{value: this.Motivaciones3,'porcentaje': this.ValMotivacion2}]
                
                
            },
            ValorMotivacion3(s){
                this.ValMotivacion3=s;
                this.Motivaciones=[{value: this.Motivaciones2,'porcentaje': this.ValMotivacion},{value: this.Motivaciones3,'porcentaje': this.ValMotivacion2},{value: this.Motivaciones4,'porcentaje': this.ValMotivacion3}]
                console.log(this.Motivaciones);
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
            console.log("NOMBRE: SI")
             
            //edad
            if (this.Edad.length < 3 && this.Edad != ""){
              console.log("EDAD: SI")
            }else{
              console.log("ESCRIBE UNA EDAD")
            }

            //Estado civil
            if (this.EstadoCivil != ""){
              console.log("ESTADO CIVIL:SI")
            }else{
              console.log("SELECCIOA UN ESTADO CIVIL")
              return false
            }

            //Trabajo
            if (this.Trabajo.length < 201 && this.Trabajo != "" && !isNaN (this.Trabajo) === false){
              console.log("TRABAJO:SI")
            }else{
              console.log("ESCRIBE UN TRABAJO")
              return false
            }

            //Residencia
            if (this.Residencia.length < 201 && this.Residencia != "" && !isNaN (this.Residencia) === false){
              console.log("RESIDENCIA:SI")
            }else{
              console.log("ESCRIBE UNA RESIDENCIA")
              return false
            }

            //Cita
            if (this.Cita.length < 501 && this.Cita != "" && !isNaN (this.Cita) === false){
              console.log("CITA :SI")
            }else{
              console.log("ESCRIBE UNA CITA")
              return false
            }

            //CitaAutor
            if (this.CitaAutor.length < 501 && this.CitaAutor != "" && !isNaN (this.CitaAutor) === false){
              console.log("CitaAutor: SI")
            }else{
              console.log("ESCRIBE UNA CitaAutor")
              return false
            }

            //Bio
            if (this.Bio.length < 701 && this.Bio != ""){
              console.log("Bio:SI")
            }else{
              console.log("ESCRIBE UNA BIO")
              return false
            }

          return true
                       
          }
          else{
            console.log("ERROR AL REGISTRAR")
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
    <div class=" bg-blue-100 rounded overflow-hidden shadow-lg">

<form class="w-full mt-6 ">
        
        <div class="grid grid-cols-2  ">

          <!-- component -->

   
    <body>
      <div class="flex justify-center items-center">
            <div class=" bg-[#d6d3d1] relative flex flex-col items-center  rounded-[20px] w-[700px] max-w-[95%] max-w-[95%] mx-auto bg-white bg-clip-border shadow-3xl shadow-shadow-500 dark:!bg-navy-800 dark:text-white dark:!shadow-none p-1">
                <div class="mt-2 mb-8 w-full">
                    <div class="relative w-full">

                     <imgUsuario/>
                      
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
                 Extrovertido: 
                 <br> 
                  {{ this.Personalidad1 }}%
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




                      <div class="">
                    <div class="md:w-1/3">
                      <label class="block text-black font-bold md:text-left my-2 md:mb-0">
               Motivaciones:
              </label>
                        
                    </div>
                    <div class="md:w-2/3">
                    
                        <TextA @inputText = "AgregarMotivaciones"  ></TextA>
                        <br> 
                       
                        <InputSlider @porcentaje="ValorMotivacion">
                        
                          
                            <h3 class="block text-black font-bold md:text-right mb-1 md:mb-0 pr-4">Porcentaje</h3>
                        
                        </InputSlider>
                    </div>
                    <div class="md:w-2/3" v-show=this.DatoAgregarMotivacion >
                        <TextA @dataA="AgregarMotivaciones2"  ></TextA>
                        <InputSliderMot @porcentaje="ValorMotivacion2">
                            
                            <h3 class="block text-black font-bold md:text-right mb-1 md:mb-0 pr-4">Porcentaje</h3>
                        
                        </InputSliderMot>
                    </div>
                    <div class="md:w-2/3" v-show=this.DatoAgregar2Motivacion >
                        <TextA  @dataA="AgregarMotivaciones3"  ></TextA>
                        <InputSliderMot @porcentaje="ValorMotivacion3">
                            
                            <h3 class="block text-black font-bold md:text-right mb-1 md:mb-0 pr-4">Porcentaje</h3>
                        
                        </InputSliderMot>
                    </div>
                    


                    <div >
                            <BotonEnviar @click="AgregarInput3(1)" class="" type="button">
                                    Agregar
                            </BotonEnviar>
                        </div>
                </div>


















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