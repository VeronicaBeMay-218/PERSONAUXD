<template>
    <div class="app-content">
      <vue-range-slider v-model="value" :min="min" :max="max" :formatter="formatter"></vue-range-slider>
    </div>
  </template>
  <script>
 
  export default {
    data() {
      return {
        value: [0, 100]
      }
    },
    components: {
      VueRangeSlider
    },
    created() {
      this.min = 0
      this.max = 250
      this.formatter = value => `￥${value}`
    }
  }
  </script> 