
<script>
export default {
    
    data() {
        return {
          estadoCivil: ""
        }
    },
    methods: {
        enviar() {
            this.$emit('person',this.estadoCivil)
        }
    }
}
</script>

<template>
    <div>
        <slot></slot>
        <br>
        <select v-model="estadoCivil" @change="enviar">
              <option value="">Seleccione</option>
              <option value="1">Soltero</option>
              <option value="2">Casado</option>
              <option value="3">Divorciado</option>
              <option value="4">Separado</option>
              <option value="5">Unió libre</option>
              <option value="6">Viudo</option>
            </select>
    </div>
</template>



