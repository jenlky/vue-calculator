<script>
import Buttons from '../components/Buttons.vue'

// JavaScript RegExp objects are stateful when they have the global or sticky flags set (e.g., /foo/g or /foo/y). 
// They store a lastIndex from the previous match. 
const regex = /\+|-|x|÷/

export default {
  components: {
    Buttons
  },
  data() {
    return {
      result: "0"
    }
  },
  methods: {
    numbersHandler (e) {
      if (this.result === "0") {
        this.result = e.currentTarget.textContent
      } else {
        this.result = this.result + e.currentTarget.textContent
      }
    },
    clearHandler () {
      this.result = "0"
    },
    clearEntryHandler () {
      if (this.result.length > 0) {
        const values = this.result.split('')
        values.splice(-1, 1)
        this.result = values.join('') || "0"
      }
    },
    lastCharIsNotOperator () {
      return !regex.test(this.result[this.result.length-2])
    },
    plusHandler () {
      if (this.lastCharIsNotOperator()) {
        this.result = this.result + " + "
      }
    },
    minusHandler () {
      if (this.lastCharIsNotOperator()) {
        this.result = this.result + " - "
      }
    },
    multiplyHandler () {
      if (this.lastCharIsNotOperator()) {
        this.result = this.result + " x "
      }
    },
    divideHandler () {
      if (this.lastCharIsNotOperator()) {
        this.result = this.result + " ÷ "
      }
    },
    equalHandler () {
      const values = this.result.split(' ')
      console.log('values', values)
      console.log('add', this.mathLogic()["+"](3, 4))

      // values.map(val => {
        
      // })
    },
    mathLogic () {
      return {
        "+": function (x, y) { return x + y },
        "-": function (x, y) { return x - y },
        "x": function (x, y) { return x * y },
        "÷": function (x, y) { return x / y }
      }
    },
  }
}
</script>

<template>
  <div>
    <h1>Vue Calculator</h1>
  </div>
  <div class="calculator">
    <div class="calculator-results">
      <span>{{ result }}</span>
    </div>
    <div class="calculator-btns">
      <div class="rows special-symbols">
        <Buttons val="%" />
        <Buttons val="√" />
        <Buttons val="CE" @click="clearEntryHandler" />
        <Buttons val="C" @click="clearHandler" />
      </div>
      <div class="rows">
        <Buttons val="7" @click="numbersHandler" />
        <Buttons val="8" @click="numbersHandler" />
        <Buttons val="9" @click="numbersHandler" />
        <Buttons val="﹣" @click="minusHandler" />
      </div>
      <div class="rows">
        <Buttons val="4" @click="numbersHandler" />
        <Buttons val="5" @click="numbersHandler" />
        <Buttons val="6" @click="numbersHandler" />
        <Buttons val="÷" @click="divideHandler" />
      </div>
      <div class="rows">
        <Buttons val="1" @click="numbersHandler" />
        <Buttons val="2" @click="numbersHandler" />
        <Buttons val="3" @click="numbersHandler" />
        <Buttons val="x" @click="multiplyHandler" />
      </div>
      <div class="rows">
        <Buttons val="0" @click="numbersHandler" />
        <Buttons val="." />
        <Buttons val="=" @click="equalHandler" />
        <Buttons val="+" @click="plusHandler" />
      </div>
    </div>
  </div>
</template>

<style>
.calculator {
  display: flex;
  flex-flow: column;
  background-color: #5DB28B;
  align-items: center;
  justify-content: center;
  padding: 20px 15px;
}

.calculator-results {
  background-color: #465965;
  color: #FFFFFF;
  width: inherit;
  margin: 0px 0px 20px;
  width: -webkit-fill-available;
  line-height: inherit;
  text-align: right;
  padding: 2px 8px;
  font-size: 22px;

  span {
    font-weight: 600;
  }
}

.rows {
  display: flex;
}

/* .special-symbols:nth-last-child(-n + 2) {
  background-color: #FFFFFF;
  color: black;
}

.rows:first-child {
  background-color: #FFFFFF !important;
  color: black;
} */
</style>
