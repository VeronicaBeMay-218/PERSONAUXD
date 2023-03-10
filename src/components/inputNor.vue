

<script>
export default {
    
    data() {
        return {
            Nor: ""
        }
    },
    methods: {
        enviar() {
            this.$emit('person',this.Nor)
        }
    }
}
</script>

<template>
    <div>
        <slot></slot>
        <br>
        <input class="appearance-none block w-full bg-gray-200 text-gray-700 border border-red-500 rounded py-3 px-4 mb-3 leading-tight focus:outline-none focus:bg-white"  id="trabajo" type="text" v-model="Nor" @change="enviar">

    </div>
</template>


