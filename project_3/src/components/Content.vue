<template>
  <div>
    <h1>Calculator</h1>
    <br />
    <div class="calculator">
      <div class="display">{{ displayResult || "0" }}</div>
      <div @click="clear()" class="clear btn">CE</div>
      <div @click="erase()" class="erase btn">←</div>
      <div
        @click="
          division();
          appendSign('/');
        "
        class="btn"
      >
        /
      </div>
      <div @click="append(1)" class="btn">1</div>
      <div @click="append(2)" class="btn">2</div>
      <div @click="append(3)" class="btn">3</div>
      <div
        @click="
          multiplication();
          appendSign('*');
        "
        class="btn"
      >
        *
      </div>
      <div @click="append(4)" class="btn">4</div>
      <div @click="append(5)" class="btn">5</div>
      <div @click="append(6)" class="btn">6</div>
      <div
        @click="
          plus();
          appendSign('+');
        "
        class="btn"
      >
        +
      </div>
      <div @click="append(7)" class="btn">7</div>
      <div @click="append(8)" class="btn">8</div>
      <div @click="append(9)" class="btn">9</div>
      <div
        @click="
          minus();
          appendSign('-');
        "
        class="btn"
      >
        -
      </div>
      <div @click="append(0)" class="btn zero">0</div>
      <div @click="equals()" class="btn result">=</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      firstNum: "",
      operator: null,
      displayResult: "",
      operatorClicked: false,
    };
  },
  methods: {
    clear() {
      this.displayResult = "";
    },
    erase() {
      this.displayResult = this.displayResult.slice(0, -1);
    },
    append(number) {
      if (this.operatorClicked) {
        this.displayResult = "";
        this.operatorClicked = false;
      }
      this.displayResult = this.displayResult + number;
    },
    appendSign(sign) {
      this.displayResult = this.displayResult + sign;
    },
    setFirst() {
      this.operatorClicked = true;
      this.firstNum = this.displayResult;
    },
    division() {
      this.operator = (a, b) => a / b;
      this.setFirst();
    },
    multiplication() {
      this.operator = (a, b) => a * b;
      this.setFirst();
    },
    plus() {
      this.operator = (a, b) => a + b;
      this.setFirst();
    },
    minus() {
      this.operator = (a, b) => a - b;
      this.setFirst();
    },
    equals() {
      this.displayResult = this.operator(
        parseFloat(this.firstNum),
        parseFloat(this.displayResult)
      );
      this.firstNum = null;
    },
  },
};
</script>

<style scoped>
.calculator {
  width: 300px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  background-color: #e2672e;
  padding: 10px 10px 10px 10px;
}
.display {
  grid-column: 1/5;
  background-color: white;
  border-radius: 15px;
  font-size: 35px;
  text-align: right;
  padding-right: 15px;
  margin-top: auto;
  overflow-wrap: break-word;
}
.btn {
  color: white;
  margin: 10px 5px 10px 5px;
  padding: 5px;
  border-radius: 5px;
  background-color: orange;
  font-size: 25px;
  cursor: pointer;
  text-align: center;
}
.clear {
  background-color: red;
  grid-column: 1/3;
}
.erase {
  background-color: rgb(96, 96, 226);
}
.result {
  background-color: rgb(105, 226, 105);
  grid-column: 3/5;
}
.zero {
  grid-column: 1/2;
}
</style>
