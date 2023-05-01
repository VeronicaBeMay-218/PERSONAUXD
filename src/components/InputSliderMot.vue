<script>
export default {
    
    data() {
        return {
            slider: 50
        }
    },
    props: {
    Datos: String
    },
    methods: {
        enviar() {
            this.$emit('porcentaje',this.slider)
        }
    }
}
</script>

<template>
    <div>
        <slot ></slot> 
        
        ({{ slider }}%)
        <br>
        <input type="range" min="0" max="100" v-model="slider" @change="enviar" class="w-full  rounded-lg transition-colors focus:shadow focus:bg-white focus:outline-none">
        <p >{{ Datos }}</p>
    </div>
</template>