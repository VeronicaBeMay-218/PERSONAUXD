<script>

export default {
    
    data() {
        return {
            porcentaje: 50
        }
    },
    methods: {
        PasarDato() {
            this.$emit('porcentaje',this.porcentaje)
        }
    }
}
</script>

<template>
    <input type="range" v-model="porcentaje" class="w-full  rounded-lg transition-colors focus:shadow focus:bg-white focus:outline-none" id="porcentaje" placeholder="" typeof="slider" min="0" max="100" @input="PasarDato"/>
</template>