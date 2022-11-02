<!-- 


- Fiks at når man trykker på operatorene skal '=' kjøre 



 -->




<template>
  <div class="calculator">
    <table class="table">
      <thead>
          <tr>
            <th colspan="4">{{ current || '0' }}</th>
          </tr>
      </thead>

      <tbody>
          <tr>
              <td v-on:click="clearField" class="tableData__grey">C</td>
              <td v-on:click="setPositiveOrNegative" class="tableData__grey">+/-</td>
              <td v-on:click="percent" class="tableData__grey">%</td>
              <td v-on:click="division" class="tableData__orange">÷</td>
          </tr>

          <tr>
              <td v-on:click="append('7')">7</td>
              <td v-on:click="append('8')">8</td>
              <td v-on:click="append('9')">9</td>
              <td v-on:click="multiplication" class="tableData__orange">x</td>
          </tr>

          <tr>
              <td v-on:click="append('4')">4</td>
              <td v-on:click="append('5')">5</td>
              <td v-on:click="append('6')">6</td>
              <td v-on:click="substraction" class="tableData__orange">-</td>
          </tr>

          <tr>
              <td v-on:click="append('1')">1</td>
              <td v-on:click="append('2')">2</td>
              <td v-on:click="append('3')">3</td>
              <td v-on:click="addition" class="tableData__orange">+</td>
          </tr>

          <tr>
              <td v-on:click="append('0')" class="tableData__zero">0</td>
              <td v-on:click="dot">.</td>
              <td v-on:click="equal" colspan="2" class="tableData__orange">=</td>
          </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      previous: null,
      current: '',
      operator: null,
      operatorClicked: false
    }
  },
  methods: {
    clearField() {
      this.current = '';
    },

    setPositiveOrNegative() {
      this.current = this.current[0] === '-' ? 
      this.current.slice(1) : `-${this.current}`;
    },

    percent() {
      this.current = `${parseFloat(this.current) / 100}`;
    },

    append(number) {
      if (this.operatorClicked) {
        this.current = '';
        this.operatorClicked = false;
      }
      this.current = `${this.current}${number}`;
    },

    dot() {
      if (this.current.indexOf('.') === -1) {
        this.append('.');
      }
    },

    setPrevious() {
      this.previous = this.current;
      this.operatorClicked = true;
    },

    division() {
      this.operator = (a, b) => a / b;
      this.setPrevious();
    },

    multiplication() {
      this.operator = (a, b) => a * b;
      this.setPrevious();
    },

    substraction() {
      this.operator = (a, b) => a - b;
      this.setPrevious();
    },

    addition() {
      this.operator = (a, b) => a + b;
      this.setPrevious();
    },

    equal() {
      this.current = `${this.operator(
        parseFloat(this.current), 
        parseFloat(this.previous)
      )}`;
      this.previous = null;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
    font-size: 20px;
    color: white;
  }

  th {
    padding: 1.5rem 1rem;
    font-size: 2.5rem;
    background-color: #4f85b775;
    border-radius: 10px;
    text-align: end;
    box-shadow: 0 0 2rem rgba(0, 0, 0, 0.265);
  }

  td {
    cursor: pointer;
    background-color: #313131;
    padding: 1rem;
    border-radius: 10px;
    box-shadow: 0 0 2rem rgba(0, 0, 0, 0.265);
  }

  td:active {
    background-color: darkgray;
  }

  .calculator {
    width: 100%;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .table {
    text-align: center;
    background-color: #225787;
    padding: 1rem;
    border-collapse: separate;
    border-spacing: .5rem;
  }

  .tableData__orange {
    background-color: #F19706;
    font-size: 1.6rem;
  }

  .tableData__orange:active {
    background-color: #313131;
  }

  .tableData__grey {
    background-color: darkgray;
    color: black;
  }

  .tableData__grey:active {
    background-color: white;
  }

  .tableData__zero {
    text-align: start;
  }
</style>
