

<script>
export default {
    
    data() {
        return {
            edad: 22
        }
    },
    methods: {
        enviar() {
            this.$emit('person',this.edad)
        }
    }
}
</script>

<template>
    <div>
        <slot></slot>
        <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500" id="grid-last-name" type="number" v-model="edad" @change="enviar">

    </div>
</template>
