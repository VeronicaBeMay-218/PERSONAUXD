<script>

export default {
    
    data() {
        return {
            datoIT: '',
        }
    },
    methods: {
        //Funcion para hacer un emit
        PasarDato() {
            
            this.$emit('dataIT',this.datoIT)
        }
    }
}
</script>

<template>
    <input type="text" v-model="datoIT" name="dataIT" id="dataIT" class="w-full py-2.5 px-4 rounded-lg bg-gray-100 focus:shadow focus:bg-white focus:outline-none" @input="PasarDato"/>
</template>
