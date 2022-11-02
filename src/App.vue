<template>
  <CalculatorIOS/>
</template>

<script>
import CalculatorIOS from '../src/components/CalculatorIOS.vue'

export default {
  name: 'App',
  components: {
    CalculatorIOS
  }
}
</script>

<style>

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-size: 20px;
    color: white;
  }
</style>
