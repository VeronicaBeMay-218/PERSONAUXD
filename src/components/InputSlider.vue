<script>
export default {
    
    data() {
        return {
            slider: 50
        }
    },
    methods: {
        enviar() {
            this.$emit('person',this.slider)
        }
    }
}
</script>

<template>
    <div>
        <slot></slot> ({{ slider }}%)
        <br>
        <input class="accent-red-500 transparent h-1.5 w-full cursor-pointer appearance-none rounded-lg border-transparent bg-neutral-200" type="range"  min="0" max="100" v-model="slider" @change="enviar">

    </div>
</template>