<template>
  <div class="calculator">
    <table class="table">
      <thead>
          <tr>
            <th colspan="3" class="table__header">{{ current || '0' }}</th>
          </tr>
      </thead>

      <tbody>
        <tr>
            <td v-on:click="append('1')" @mouseenter="hover = true"
                @mouseleave="hover = false" :class="{ 'td:hover': hover }">1</td>
            <td v-on:click="append('2')">2</td>
            <td v-on:click="append('3')">3</td>
          </tr>
          
          <tr>
            <td v-on:click="append('4')">4</td>
            <td v-on:click="append('5')">5</td>
            <td v-on:click="append('6')">6</td>
          </tr>
          
          <tr>
            <td v-on:click="append('7')">7</td>
            <td v-on:click="append('8')">8</td>
            <td v-on:click="append('9')">9</td>
          </tr>
          
          <tr>
            <td v-on:click="append('0')">0</td>
            <td v-on:click="addition('+')">+</td>
            <td v-on:click="substraction('-')">-</td>
          </tr>
          
          <tr>
            <td v-on:click="division('/')">÷</td>
            <td v-on:click="multiplication('*')">x</td> 
            <td v-on:click="dot">.</td>
          </tr>
          
          <tr>
            <td v-on:click="clearField" >C</td>
            <td v-on:click="equal" colspan="2">=</td>
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
      operatorClicked: false,
      hover: false,
    }
  },

  created() {
			window.addEventListener('keyup', this.handleKeyup);
		},

    computed: {
      currentAsNumber() {
        return Number(this.current)
      },

      previousAsNumber() {
        return Number(this.previous)
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
      this.current = `${this.currentAsNumber / 100}`;
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
      this.operator = (a, b) => b / a;
      this.setPrevious();
    },

    multiplication() {
      this.operator = (a, b) => b * a;
      this.setPrevious();
    },

    substraction() {
      this.operator = (a, b) => b - a;
      this.setPrevious();
    },

    addition() {
      this.operator = (a, b) => b + a;
      this.setPrevious();
    },

    equal() {
      this.current = `${this.operator(this.currentAsNumber, this.previousAsNumber
      )}`;
      this.previous = null;
    },

    handleKeyup(event) {
				switch(event.key) {
					case '0':
					case '1':
					case '2':
					case '3':
					case '4':
					case '5':
					case '6':
					case '7':
					case '8':
					case '9':
            this.append(event.key);
            break;
					case '+':
            this.addition(event.key);
            break;
					case '-':
            this.substraction(event.key);
            break;
					case '/':
            this.division(event.key);
            break;
					case '*':
            this.multiplication(event.key);
            break;
					case '.':
            this.dot(event.key);
            break;
					case '%':
            this.percent(event.key);
						break;
					case '=':
					case 'Enter':
						this.equal()
						break;
					case 'Escape':
					case 'Backspace':
						this.clearField()
						break;
				}
			}
  }
}
</script>


<style scoped>

  th {
    padding: 2rem;
    font-size: 2.5rem;
    background-color: var(--background);
    border-radius: 10px;
    text-align: end;
  }

  td {
    position: relative;
    padding: 1rem 2rem;
    border-radius: 10px;
    background-color: var(--background);
    cursor: pointer;
  }

  td:hover {
    background-color: yellow;
    color: black;
    transition: .3s;
  }

  .calculator {
    width: 100%;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background: linear-gradient(0deg, rgba(0, 0, 0, 0.815), 
    rgba(0, 0, 0, 0.801)), url(../assets/wallpaper.jpg);
    --background: rgba(177, 163, 163, 0.1);
  }

  .table {
    text-align: center;
    padding: 1rem;
    border-collapse: separate;
    border-spacing: .5rem;
    background-color: var(--background);
  }
</style>
