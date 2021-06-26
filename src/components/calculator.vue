<template>
  <div id="app">
    <div class="containerSquare">
      <div class="whiteSquare">
        <input v-model="currentNumber" />
      </div>
    </div>
    <div class="buttons">
      <button @click="adding('7')">7</button>
      <button @click="adding('8')">8</button>
      <button @click="adding('9')">9</button>
      <button @click="erase">del</button>
      <button @click="adding('4')">4</button>
      <button @click="adding('5')">5</button>
      <button @click="adding('6')">6</button>
      <button @click="dividir('/')">/</button>
      <button @click="adding('1')">1</button>
      <button @click="adding('2')">2</button>
      <button @click="adding('3')">3</button>
      <button @click="multiplication">*</button>
      <button @click="sustraction('-')">-</button>
      <button @click="adding('0')">0</button>
      <button @click="equal">=</button>
      <button @click="sum">+</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
      currentNumber: "",
      previousNumber: 0,
      sign: [],
    };
  },

  methods: {
    adding(number) {
      this.currentNumber = this.currentNumber + number;
      parseInt(this.currentNumber);
    },
    erase() {
      this.currentNumber = "";
    },
    equal() {
      let valor = this.sign[this.sign.length - 1];
      if (valor == "+") {
        this.currentNumber =
          parseInt(this.currentNumber) + parseInt(this.previousNumber);
        this.previousNumber = 0;
      }
      if (valor == "-") {
        this.currentNumber = this.previousNumber - parseInt(this.currentNumber);
        this.previousNumber = 0;
      }
      if (valor == "*") {
        this.currentNumber = parseInt(this.currentNumber) * this.previousNumber;
        this.previousNumber = 0;
      }
      if (valor == "/") {
        this.currentNumber = this.previousNumber / parseInt(this.currentNumber);
        this.previousNumber = 0;
      }
    },
    minusSign() {
      this.previousNumber =
        parseInt(this.previousNumber) - parseInt(this.currentNumber);
      this.currentNumber = "";
    },
    xSign() {
      this.previousNumber =
        parseInt(this.previousNumber) * parseInt(this.currentNumber);
      this.currentNumber = "";
    },
    divSign() {
      this.previousNumber =
        parseInt(this.previousNumber) / parseInt(this.currentNumber);

      this.currentNumber = "";
    },
    sumSign() {
      this.previousNumber = this.previousNumber + this.currentNumber;
      this.currentNumber = "";
    },
    sum() {
      this.sign.push("+");

      if (this.sign[0] == "-") {
        this.minusSign();
        this.sign[0] = "+";
      }

      if (this.sign[0] == "*") {
        this.xSign();
        this.sign[0] = "+";
      }
      if (this.sign[0] == "/") {
        this.divSign();
        this.sign[0] = "+";
      }

      if (this.previousNumber == 0) {
        this.previousNumber = parseInt(this.currentNumber);
        this.currentNumber = "";
      } else {
        this.sumSign();
      }
    },

    multiplication() {
      this.sign.push("*");

      if (this.sign[0] == "-") {
        this.minusSign();
        this.sign[0] = "*";
      }
      if (this.sign[0] == "+") {
        this.sumSign();
        this.sign[0] = "*";
      }
      if (this.sign[0] == "/") {
        this.divSign();
        this.sign[0] = "*";
      }

      if (this.previousNumber == 0) {
        this.previousNumber = parseInt(this.currentNumber);
        this.currentNumber = "";
      } else {
        if (this.currentNumber == "") {
          this.currentNumber = 1;
        }

        this.xSign();
      }
    },
    dividir() {
      this.sign.push("/");
      if (this.sign[0] == "-") {
        this.minusSign();
        this.sign[0] = "/";
      }
      if (this.sign[0] == "+") {
        this.sumSign;
        this.sign[0] = "/";
      }
      if (this.sign[0] == "*") {
        this.xSign();
        this.sign[0] = "/";
      }

      if (this.previousNumber == 0) {
        this.previousNumber = this.currentNumber;
        this.currentNumber = "";
      } else {
        if (this.currentNumber == "") {
          this.currentNumber = 1;
        }
        this.divSign();
      }
    },
    sustraction() {
      this.sign.push("-");

      if (this.sign[0] == "+") {
        this.sumSign();
        this.sign[0] = "-";
      }

      if (this.sign[0] == "*") {
        this.xSign();
        this.sign[0] = "-";
      }
      if (this.sign[0] == "/") {
        this.divSign();
        this.sign[0] = "-";
      }

      if (this.previousNumber == 0) {
        this.previousNumber = parseInt(this.currentNumber);
        this.currentNumber = "";
      } else {
        this.minusSign();
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
html {
  background-color: #3b93c7;
}
.whiteSquare {
  width: 360px;
  height: 150px;
  background: black;
}
.containerSquare {
  display: flex;
  justify-content: center;
}
.buttons {
  display: grid;
  grid-template-columns: 90px 90px 90px 90px;

  justify-content: center;
}
button {
  height: 70px;
  padding: 20px;
  border: none;
}
input {
  background: black;
  border: none;
  color: white;
  margin-top: 120px;
  width: 350px;
  text-align: end;
}
</style>