<template>
  <CalculatorIOS/>
  <LengthConverter/>
</template>

<script>
import CalculatorIOS from '../src/components/CalculatorIOS.vue'
import LengthConverter from './components/LengthConverter.vue';

export default {
  name: 'App',
  components: {
    CalculatorIOS,
    LengthConverter
  }
}
</script>

<style>

  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-size: 20px;
    font-family: sans-serif;
    color: white;
  }
</style>
