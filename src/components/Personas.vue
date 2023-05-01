<script>


import imagenChica from '../components/imagenChica.vue';
import imgUsuario from '../components/imgUsuario.vue';
import axios from 'axios'

let API_URL = '/api/getPersonasUxd.php'

export default {

  components:{
    //nombre con el que se llama a los componentes
    imagenChica, imgUsuario, //InputArray2
  },

  data() {
    return {

      showModal: false,
      showModal2: false,
      //variables de retorno  
      //para lista de personas
      personas: [],
      infoUno: [],


      //para ocultar y mostrar
      mostrarLista: true,
      mostrarBuscados: false,
      mostrarUno:false,
      nohay:false,

      //para el buscador
      buscar:"",
      buscados:[]
    }
  },
  mounted() {
    axios
      .get(API_URL)
        .then((response) => {
        
        //lista como en el json
        this.personas = response.data.personas
        console.log (this.personas)
    })
    
  },
  methods: {
    //funcion para buscar personas por id
    buscador(buscar) { 

      //si esta vacio
      if(buscar==""){
        //muestra la lista
        this.mostrarLista= true
        //oculta la tarjeta de buscados
        this.mostrarBuscados = false
        //oculta mensaje no hay
        this.nohay=false
      }
      //sino
      else{
               
        //si es numerico
        if(!isNaN (buscar) === true) {
          //busca en el servidor por url
          API_URL='/api/getPersonasUxd.php?id='+ buscar

          //metodo get
          axios.get(API_URL) 
          //si hay error entonces
          .catch(error => {
            //oculta la card del buscado
            this.mostrarBuscados = false

            //muestra mensaje que no existe el id que busca
            this.nohay = true
          })
          //si no hay errores guarda todo lo que recibe 
          .then((response) => {
            //llamando a los datos del json extraido
            this.buscados = response.data.persona;
            //mostrando buscados en consola
            console.log(this.buscados)
            //mostramos cards buscados
            this.mostrarBuscados = true
            //deshabilitamos mensaje no existe
            this.nohay = false
            console.log(this.nohay)
          })         
        
          //cambiamos a verdadero que recibe por nombre 
          this.nohay=true           
        } 
          
      }
      
    },

    //informacion de una persona
    InfoPer(id) {     
      //url de consumo API
      API_URL='/api/getPersonasUxd.php?id='+id 
      console.log(API_URL)

      //lo obtiene
      axios.get(API_URL)

      //tomamos la respuesta
      .then((response) => {
        console.log(response) //regresa datos de una sola persona
        //contiene el array de cada persona con sus datos
        this.infoUno = response.data.persona;
        if (this.infoUno.estadoCivil== 1){
          this.infoUno.estadoCivil= "Soltero"
        }
        if (this.infoUno.estadoCivil== 2){
          this.infoUno.estadoCivil= "Casado"
        }
        if (this.infoUno.estadoCivil== 3){
          this.infoUno.estadoCivil= "Divorciado"
        }
        if (this.infoUno.estadoCivil== 4){
          this.infoUno.estadoCivil= "Separado"
        }
        if (this.infoUno.estadoCivil== 5){
          this.infoUno.estadoCivil= "Unión libre"
        }
        if (this.infoUno.estadoCivil== 6){
          this.infoUno.estadoCivil= "Viudo"
        }
        console.log(this.infoUno)
         
      })

      //el id incrementa
      this.id++
      //cambiamos el valor por verdadero para que lo muestre
      this.mostrarUno=true
      //console.log(this.mostrarUno)
       
    },
  }

}
</script>

<template>

  <!--Buscador-->
  <div class="">
    <label for="">Buscar:</label>
    <input class="w-full appearance-none text-black text-opacity-100 rounded shadow py-1 px-2 mr-2 focus:outline-none focus:shadow-outline focus:border-blue-200 text-opacity-25 " type="text" v-model="buscar"  placeholder="Buscar por id" @input = "showModal2= true , buscador(buscar)">

  </div>


  
  <!--Resultado de Buscador-->





  <Transition name="fad">
<div class="modal" v-if="showModal2">
  <!--si no recibe true en la variable mostrarBuscados
      ENCONTRO VARIOS PERSONAS POR SU ID-->
      <div v-if="mostrarBuscados" class="m-auto w-3/4 mb-5">
   
   <!--Recorre la nueva lista y por cada personaje que encuentra-->    
   <!--carta de personaje-->      




   <form class="w-full mt-6 bg-[#d6d3d1]">
        
        <div class="grid grid-cols-2  ">
   <body>
     
            <div class="bg-[#d6d3d1] relative flex flex-col items-center  rounded-[20px] w-[700px] max-w-[95%] max-w-[95%] mx-auto bg-white bg-clip-border shadow-3xl shadow-shadow-500 dark:!bg-navy-800 dark:text-white dark:!shadow-none p-1">
                <div class="mt-2 mb-8 w-full">
                    <div class="relative w-full">

                      <imgUsuario></imgUsuario>
                      
                    </div>
                    <div class="mb-3 flex items-center justify-between px-1 md:items-start">
                      <div class="w-full">
              
              
      <div class="w-full mt-4   rounded-md ">
       

       <h2 class="mb-1 px-3"> <b>Id: </b> {{ buscados.id }}</h2>
       <h2 class="mb-1 px-3"> <b>Nombre:</b> {{ buscados.nombre }}</h2>
       <h4 class="mb-1 px-3"> <b>Edad:</b> {{ buscados.edad}}</h4>
       <h4 class="mb-1 px-3"> <b>Estado Civil:</b> {{ buscados.estadoCivil}}</h4>
       <h4 class="mb-1 px-3"> <b>Trabajo:</b> {{ buscados.trabajo }}</h4>
       <h4 class="mb-1 px-3"> <b>Residencia:</b> {{ buscados.residencia}}</h4>
     </div>
            </div>
          </div>

          <div class="mb-2 flex items-center justify-between px-1 md:items-start">
                       <!-- Cita -->
     <div class="w-full mt-4  rounded-md">
       
       <h4 class="mb-1 px-3"> <b>Cita:</b> <br> {{ buscados.cita}}</h4>
       
       
     </div>

     <div class="w-full mt-4  rounded-md">
       
       <h4 class="mb-1 px-3"> <b>Autor:</b> {{ buscados.citaAutor}}</h4>
       
     </div>

    </div>
     





          <div class="mb-3 flex items-center justify-between px-1 md:items-start">
            <div class="w-full mt-4">


            
     <!-- Motivaciones -->
     <div class="w-full mt-4  bg-gray-100 rounded-md">
       
       <h1 class="text-2xl  text-center font-bold  text-black">Motivaciones</h1>
       
       <!-- recorro array de frustraciones y llamo a index -->
       <div class="w-full mt-4 mx-auto px-3" v-for="f,index in buscados.motivaciones">

         <label class=" text-black font-bold md:text-left my-2 md:mb-0">
             Motivaciones {{ index +1 }}:
             <br>
         </label>

         <h4 class="mb-1 px-3">{{ f.motivacion }}</h4>

       </div>

     </div>
           
     <!-- Marcas -->
     <div class="w-full mt-4 bg-gray-100 rounded-md">
       
       <h1 class="text-2xl  text-center font-bold  text-black">Marcas</h1>
       
       <!-- recorro array de frustraciones y llamo a index -->
       <div class="w-full mt-4 mx-auto px-3" v-for="m,index in buscados.marcas">

         <label class=" text-black font-bold md:text-left my-2 md:mb-0">
             Marca {{ index +1 }}:
             <br>
         </label>

         <h4 class="mb-1 px-3">{{ m.marca }}</h4>

       </div>

     </div>
              </div>
          </div>


                    <div class="flex items-center justify-between md:items-center lg:justify-between ">
                        
                       </div>
               
            </div>
            </div>
</body>
          
          <!-- Personalidades  -->
          <div class=" p-3 rounded-lg w-full ">

            <!-- component -->

   
<body >
        
                <div class="mt-2 mb-8 w-full">

                    <p class="mt-2 px-2 text-base text-gray-600">


                   <!-- Biografia -->
          <!-- Personal -->
     <div class="w-full mt-4  bg-indigo-100 rounded-md">
       
       <h1 class="text-2xl  text-center font-bold  text-black">Biografía</h1>
         
       <h4 class="mb-1 px-3"> <b>Yo:</b> <br>{{ buscados.bio}}</h4>
     </div>


                    </p>



                </div> 





                <div class="grid grid-cols-2 gap-4 px-2 w-full">


                  <div class="flex flex-col justify-center rounded-2xl bg-white bg-clip-border px-3 py-4 shadow-3xl shadow-shadow-500 dark:!bg-navy-700 dark:shadow-none">
                    <p class=" text-gray-600">Personalidades</p>
                    <p class="text-base font-medium text-navy-700 dark:text-white">
                      <div class="w-full mt-4">
                        <div class="w-full mt-4 mx-auto px-3 ">
        

         <div class="flex  justify-between">
           <label class="text-black  md:text-left my-2 md:mb-0">
             Extrovertido: <br>  {{buscados.personalidad01 }}%
           </label>
           
           <label class="text-black  text-end  mr-0 md:text-right my-2 md:mb-0">
             Introvertido: <br> {{ 100 - buscados.personalidad01}}%
           </label>
         </div>

         <div class=" px-4">
         <input type="range" v-model="buscados.personalidad01" class="w-full -3 py-3 mx-auto rounded-lg transition-colors bg-gray-100 focus:shadow focus:bg-white focus:outline-none" id="porcentaje" placeholder="" typeof="slider" min="0" max="100"/>
         </div>

       </div>

       <div class="w-full mt-4 mx-auto px-3">
           

           <div class="flex  justify-between">
             <label class="text-black  text-left md:text-left my-2 md:mb-0">
              Organizado: <br>  {{buscados.personalidad02 }}%
             </label>
             
             <label class="text-black  text-end  mr-0 md:text-right my-2 md:mb-0">
              Desordenado: <br> {{ 100 - buscados.personalidad02}}%
             </label>
           </div>
           <div class=" px-4">
           <input type="range" v-model="buscados.personalidad02" class="w-full -3 py-3 mx-auto rounded-lg transition-colors bg-gray-100 focus:shadow focus:bg-white focus:outline-none" id="porcentaje" placeholder="" typeof="slider" min="0" max="100"/>
           </div>

   

            
            </div>
          </div>
                    </p>
                    </div>

                    <div class="flex flex-col justify-center rounded-2xl bg-white bg-clip-border px-3 py-4 shadow-3xl shadow-shadow-500 dark:!bg-navy-700 dark:shadow-none">
                    <p class=" text-gray-600">Personalidades</p>
                    <p class="text-base font-medium text-navy-700 dark:text-white">
                      <div class="w-full">
              

                        <div class="w-full mt-4 mx-auto px-3">
         

         <div class="flex  justify-between px-4">
           <label class="text-black  text-left md:text-left my-2 md:mb-0">
            Creativo: <br>  {{buscados.personalidad03 }}%
           </label>
           
           <label class="text-black  text-end  mr-0 md:text-right my-2 md:mb-0">
            Analítico: <br> {{ 100 - buscados.personalidad03}}%
           </label>
         </div>
         <div class=" px-3">
         <input type="range" v-model="buscados.personalidad03" class="w-full -3 py-3 mx-auto rounded-lg transition-colors bg-gray-100 focus:shadow focus:bg-white focus:outline-none" id="porcentaje" placeholder="" typeof="slider" min="0" max="100"/>
         </div>

       </div>

       <div class="w-full mt-4 mx-auto px-3">
         

         <div class="flex  justify-between px-3">
           <label class="text-black  text-left md:text-left my-2 md:mb-0">
            Rico en tiempo: <br>  {{buscados.personalidad04 }}%
           </label>
           
           <label class="text-black  text-end  mr-0 md:text-right my-2 md:mb-0">
            Ocupado: <br> {{ 100 - buscados.personalidad04}}%
           </label>
         </div>
         <div class=" px-3">
         <input type="range" v-model="buscados.personalidad04" class="w-full -3 py-3 mx-auto rounded-lg transition-colors bg-gray-100 focus:shadow focus:bg-white focus:outline-none" id="porcentaje" placeholder="" typeof="slider" min="0" max="100"/>
         </div>





        </div>

                      </div>
                    </p>
                    </div>



  <div class="flex flex-col items-start justify-center rounded-2xl bg-white bg-clip-border px-3 py-4 shadow-3xl shadow-shadow-500 dark:!bg-navy-700 dark:shadow-none">
                    
                    <p class="text-base font-medium text-navy-700 dark:text-white">
                        
 <!-- Objetivos -->
 <div class="w-full mt-4  rounded-md">
       
       <h1 class="text-2xl  text-center font-bold  text-black">Objetivos</h1>
       
       <!-- recorro array de objetivos y llamo a index -->
       <div class="w-full mt-4 mx-auto px-3" v-for="o,index in buscados.objetivos">

         <label class=" text-black font-bold md:text-left my-2 md:mb-0">
             Objetivo {{ index +1 }}:
             <br>
         </label>

         <h4 class="mb-1 px-3">{{ o.objetivo }}</h4>

       </div>

     </div>


      </p>
  </div>



  <div class="flex flex-col rounded-2xl bg-white bg-clip-border px-3 py-4 shadow-3xl shadow-shadow-500 dark:!bg-navy-700 dark:shadow-none">
                    
                    
 <!-- Frustraciones -->
 <div class="w-full mt-4  rounded-md">
       
       <h1 class="text-2xl  text-center font-bold  text-black">Frustraciones</h1>
       
       <!-- recorro array de frustraciones y llamo a index -->
       <div class="w-full mt-4 mx-auto px-3" v-for="f,index in buscados.frustraciones">

         <label class=" text-black font-bold md:text-left my-2 md:mb-0">
             Frustración {{ index +1 }}:
             <br>
         </label>

         <h4 class="mb-1 px-3">{{ f.frustracion }}</h4>

       </div>

     </div>
            

 </div>

 

                   
                </div>
           
            
           
  </body>
</div>


</div>
</form>   
   

</div>


<button @click="showModal2= false">Cerrar</button>
</div>


</Transition>

   







 <!--si no existe el id buscado-->
 <div v-if="nohay" class="mx-auto">

   <!--Muestra mensaje de no existe-->
   <h1 class="text-center text-xl my-5">
     No existe el usuario que buscas :0
   </h1>

 </div>













<!------------------------------------------------------------------------------------->
<!--CARDS DE PERSONAS-->
  <!--Recorre la nueva lista y por cada personaje que encuentra-->    
  <div class="grid  mx-auto p-1 border-4 rounded-lg  border-red-50 ">

<h1 class="text-center text-white text-4xl font-bold my-4"> Lista de Personas</h1><br>

<div class="" >
    

  <div class="shadow-2xl">

    <div class="text-center" >
    <div class="flex items-center font-bold ... w-120 rounded overflow-hidden shadow-lg p-12 m-10 snap-start bg-[]">
  <body class="antialiased bg-gray-200 text-gray-900 font-sans p-6">


    <div class="flex flex-wrap justify-center">

  <ul class="p-5 grid grid-cols-1 sm:grid-cols-1 md:grid-cols-3 lg:grid-cols-3 xl:grid-cols-6 gap-5">
  

      <li v-for="(p, index) in personas" class="text-sm w-120 rounded-full overflow-visible shadow-lg p- m-1 snap-start bg-[#bfdbfe]">
        <h1 class=" px-6 py-4 font-medium text-blue-900 whitespace-nowrap dark:text-blue-100"> {{ index += 1 }} </h1>
        <imagenChica></imagenChica>

    <a>id:{{ p.id }} {{ p.nombre }} </a> 
   
          <h1 class=" px-6 py-4 font-medium  whitespace-nowrap dark:text-blue-100">{{ p.nombre }}</h1>
          
            <button @click="showModal= true , InfoPer(p.id) ">Ver</button>

          
  </li> 
        
    
    </ul>
  </div>
  </body>


     
</div>

   </div>
  </div>



  <Transition name="fad">
<div class="modal" v-if="showModal">




   <!--Informacion sólo Uno-->
   <div class=" py-15"  v-if="mostrarUno">
     
     <!--carta de personaje-->          
     <div class="w-3/4 mx-auto px-5 my-16 border-4 border-indigo-50  bg-white rounded-sm">





  <form class="w-full mt-6 bg-[#d6d3d1]">
        
        <div class="grid grid-cols-2  ">
   <body>
     
            <div class="bg-[#d6d3d1] relative flex flex-col items-center  rounded-[20px] w-[700px] max-w-[95%] max-w-[95%] mx-auto bg-white bg-clip-border shadow-3xl shadow-shadow-500 dark:!bg-navy-800 dark:text-white dark:!shadow-none p-1">
                <div class="mt-2 mb-8 w-full">
                    <div class="object-top">

                      <imgUsuario></imgUsuario>
                      
                    </div>
                    <div class="mb-3 flex items-center justify-between px-1 md:items-start">
                      <div class="w-full">
              
              
      <div class="w-full mt-4   rounded-md ">
       

        <div class="w-full mt-4 rounded-md">
         
     
         <h2 class="mb-1 px-3"> <b>Id: </b> {{ infoUno.id }}</h2>
         <h2 class="mb-1 px-3"> <b>Nombre:</b> {{ infoUno.nombre }}</h2>
         <h4 class="mb-1 px-3"> <b>Edad:</b> {{ infoUno.edad}}</h4>
         <h4 class="mb-1 px-3"> <b>Estado Civil:</b> {{ infoUno.estadoCivil}}</h4>
         <h4 class="mb-1 px-3"> <b>Trabajo:</b> {{ infoUno.trabajo }}</h4>
         <h4 class="mb-1 px-3"> <b>Residencia:</b> {{ infoUno.residencia}}</h4>
       </div>

     </div>
            </div>
          </div>

          <div class="mb-2 flex items-center justify-between px-1 md:items-start">
                      

          <!-- Cita -->
       <div class="w-full mt-4  rounded-md">
         <h1 class="text-2xl  text-center font-bold  text-black"></h1>
         <h4 class="mb-1 px-3"> <b>Cita:</b> <br> {{ infoUno.cita}}</h4>
         
         
       </div>


     <div class="w-full mt-4  rounded-md">
       
       <!-- Cita -->
       <div class="w-full mt-4 rounded-md">
         <h1 class="text-2xl  text-center font-bold  text-black"></h1>
       
         <h4 class="mb-1 px-3"> <b>Autor:</b> {{ infoUno.citaAutor}}</h4>
         
       </div>

       
     </div>

    </div>
     





          <div class="mb-3 flex items-center justify-between px-1 md:items-start">
            <div class="w-full mt-4">


            
     <!-- Motivaciones -->
    
     <div class="w-full mt-4  bg-gray-100 rounded-md">
         
         <h1 class="text-2xl  text-center font-bold  text-black">Motivaciones</h1>
         
         <!-- recorro array de frustraciones y llamo a index -->
         <div class="w-full mt-4 mx-auto px-3" v-for="f,index in infoUno.motivaciones">

           <label class=" text-black font-bold md:text-left my-2 md:mb-0">
               Motivación {{ index +1 }}:
               <br>
           </label>

           <h4 class="mb-1 px-3">{{ f.motivacion }}</h4>

         </div>

       </div>



      <!-- Marcas -->
      <div class="w-full mt-4 bg-gray-100 rounded-md">
         
         <h1 class="text-2xl  text-center font-bold  text-black">Marcas</h1>
         
         <!-- recorro array de frustraciones y llamo a index -->
         <div class="w-full mt-4 mx-auto px-3" v-for="m,index in infoUno.marcas">

           <label class=" text-black font-bold md:text-left my-2 md:mb-0">
               Marca {{ index +1 }}:
               <br>
           </label>

           <h4 class="mb-1 px-3">{{ m.marca }}</h4>

         </div>

       </div>



              </div>
          </div>


                    <div class="flex items-center justify-between md:items-center lg:justify-between ">
                        
                       </div>
               
            </div>
            </div>
</body>
          
          <!-- Personalidades  -->
          <div class=" p-3 rounded-lg w-full ">

            <!-- component -->

   
<body >
        
                <div class="mt-2 mb-8 w-full">

                    <p class="mt-2 px-2 text-base text-gray-600">


                   <!-- Biografia -->
          <!-- Personal -->
     <!-- Personal -->
     <div class="w-full mt-4  bg-indigo-100 rounded-md">
         
         <h1 class="text-2xl  text-center font-bold  text-black">Biografía</h1>
           
         <h4 class="mb-1 px-3"> <b>Yo:</b> <br>{{ infoUno.bio}}</h4>
       </div>



                    </p>



                </div> 





                <div class="grid grid-cols-2 gap-4 px-2 w-full">


                  <div class="flex flex-col justify-center rounded-2xl bg-white bg-clip-border px-3 py-4 shadow-3xl shadow-shadow-500 dark:!bg-navy-700 dark:shadow-none">
                    <p class=" text-gray-600">Personalidades</p>
                    <p class="text-base font-medium text-navy-700 dark:text-white">


<div class="w-full">


<div class="w-full mt-4 mx-auto">
        

  <div class="flex  justify-between">
             <label class="text-black  text-left md:text-left my-2 md:mb-0">
               Extrovertido: <br>  {{infoUno.personalidad01 }}%
             </label>
             
             <label class="text-black  text-end  mr-0 md:text-right my-2 md:mb-0">
               Introvertido: <br> {{ 100 - infoUno.personalidad01}}%
             </label>
           </div>

           <div class=" px-4">
           <input type="range" v-model="infoUno.personalidad01" class="w-full -3 py-3 mx-auto rounded-lg transition-colors bg-gray-100 focus:shadow focus:bg-white focus:outline-none" id="porcentaje" placeholder="" typeof="slider" min="0" max="100"/>
           </div>

 </div>



<div class="w-full mt-4 mx-auto">
           

  <div class="flex  justify-between">
               <label class="text-black  text-left md:text-left my-2 md:mb-0">
                Organizado: <br>  {{infoUno.personalidad02 }}%
               </label>
               
               <label class="text-black  text-end  mr-0 md:text-right my-2 md:mb-0">
                Desordenado: <br> {{ 100 - infoUno.personalidad02}}%
               </label>
             </div>
             <div class=" px-4">
             <input type="range" v-model="infoUno.personalidad02" class="w-full -3 py-3 mx-auto rounded-lg transition-colors bg-gray-100 focus:shadow focus:bg-white focus:outline-none" id="porcentaje" placeholder="" typeof="slider" min="0" max="100"/>
             </div>

  </div>



          </div>
                    </p>
                    </div>

                    <div class="flex flex-col justify-center rounded-2xl bg-white bg-clip-border px-3 py-4 shadow-3xl shadow-shadow-500 dark:!bg-navy-700 dark:shadow-none">
                    <p class=" text-gray-600">Personalidades</p>
                    <p class="text-base font-medium text-navy-700 dark:text-white">
                      <div class="w-full">
              

  <div class="w-full mt-4 mx-auto px-3">
         

    <div class="flex  justify-between px-4">
             <label class="text-black  text-left md:text-left my-2 md:mb-0">
              Creativo: <br>  {{infoUno.personalidad03 }}%
             </label>
             
             <label class="text-black  text-end  mr-0 md:text-right my-2 md:mb-0">
              Analítico: <br> {{ 100 - infoUno.personalidad03}}%
             </label>
           </div>
           <div class=" px-3">
           <input type="range" v-model="infoUno.personalidad03" class="w-full -3 py-3 mx-auto rounded-lg transition-colors bg-gray-100 focus:shadow focus:bg-white focus:outline-none" id="porcentaje" placeholder="" typeof="slider" min="0" max="100"/>
           </div>

</div>

       <div class="w-full mt-4 mx-auto px-3">
         

        <div class="flex  justify-between px-3">
             <label class="text-black  text-left md:text-left my-2 md:mb-0">
              Rico en tiempo: <br>  {{infoUno.personalidad04 }}%
             </label>
             
             <label class="text-black  text-end  mr-0 md:text-right my-2 md:mb-0">
              Ocupado: <br> {{ 100 - infoUno.personalidad04}}%
             </label>
           </div>
           <div class=" px-3">
           <input type="range" v-model="infoUno.personalidad04" class="w-full -3 py-3 mx-auto rounded-lg transition-colors bg-gray-100 focus:shadow focus:bg-white focus:outline-none" id="porcentaje" placeholder="" typeof="slider" min="0" max="100"/>
           </div>





        </div>

                      </div>
                    </p>
                    </div>



  <div class="flex flex-col items-start justify-center rounded-2xl bg-white bg-clip-border px-3 py-4 shadow-3xl shadow-shadow-500 dark:!bg-navy-700 dark:shadow-none">
                    
                    <p class="text-base font-medium text-navy-700 dark:text-white">
                        
  <!-- Objetivos -->
  <div class="w-full mt-4  rounded-md">
         
         <h1 class="text-2xl  text-center font-bold  text-black">Objetivos</h1>
         
         <!-- recorro array de objetivos y llamo a index -->
         <div class="w-full mt-4 mx-auto px-3" v-for="o,index in infoUno.objetivos">

           <label class=" text-black font-bold md:text-left my-2 md:mb-0">
               Objetivo {{ index +1 }}:
               <br>
           </label>

           <h4 class="mb-1 px-3">{{ o.objetivo }}</h4>

         </div>

       </div>


      </p>
  </div>



  <div class="flex flex-col rounded-2xl bg-white bg-clip-border px-3 py-4 shadow-3xl shadow-shadow-500 dark:!bg-navy-700 dark:shadow-none">
                    
                    
 <!-- Frustraciones -->
 <div class="w-full mt-4 rounded-md">
         
         <h1 class="text-2xl  text-center font-bold  text-black">Frustracionees</h1>
         
         <!-- recorro array de frustraciones y llamo a index -->
         <div class="w-full mt-4 mx-auto px-3" v-for="f,index in infoUno.frustraciones">

           <label class=" text-black font-bold md:text-left my-2 md:mb-0">
               Frustración {{ index +1 }}:
               <br>
           </label>

           <h4 class="mb-1 px-3">{{ f.frustracion }}</h4>

         </div>

       </div>
            

 </div>

 

                   
                </div>
           
            
           
  </body>
</div>


</div>
</form>   


     
      

           

         </div>
       </div>

      


<button @click="showModal= false">Cerrar</button>
</div>


</Transition>

  </div>















       
              
      



       

     </div>

  

</template>



<style>
*{
margin:0;
padding: 0;

}

#app{

width: 100%;
height: 100%;
overflow: hidden;

}

.modal{
  position: absolute;
  top: 50%;
  left: 0%;
  transform: translate(-50,-50);
  background: #cac2c2 ;
  padding: 20px;
  border-radius: 15px;
  box-shadow: 3px 3px rgba(0, 0, 0, 0.4);
  z-index: 101;

}


</style>