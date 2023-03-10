


<script>
export default {
    
    data() {
        return {
          nombre: "vero"
        }
    },
    methods: {
        enviar() {
            this.$emit('person',this.nombre)
        }
    }
}
</script>

<template>
    <div>
        <slot></slot> 
        <br>
        <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white" id="grid-first-name" type="text" placeholder="vero be"  v-model="nombre" @change="enviar">

    </div>
</template>




