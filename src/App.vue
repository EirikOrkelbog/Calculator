<template>
  <CalculatorIOS/>
</template>

<script>
import CalculatorIOS from '../src/components/CalculatorIOS.vue'
// import UnitCalculator from './components/UnitCalculator.vue';

export default {
  name: 'App',
  components: {
    CalculatorIOS,
    // UnitCalculator
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
