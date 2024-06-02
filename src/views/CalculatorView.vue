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
      const value = e.currentTarget.textContent
      if (this.result === "0" && value !== ".") {
        this.result = value
      } else {
        this.result = this.result + value
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
        this.result = this.result + " * "
      }
    },
    divideHandler (e) {
      if (this.lastCharIsNotOperator()) {
        this.result = this.result + ` ${e.target.value} `
      }
    },
    equalHandler () {
      // const values = this.result.split(' ')
      // console.log('values', values)
      // console.log('add', this.mathLogic()["+"](3, 4))

      console.log(this.result)
      console.log(eval(this.result))

      this.result = eval(this.result)
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
        <Buttons display="%" val="%" />
        <Buttons display="√" val="√" />
        <Buttons display="CE" val="CE" @click="clearEntryHandler" />
        <Buttons display="C" val="C" @click="clearHandler" />
      </div>
      <div class="rows">
        <Buttons display="8" val="8" @click="numbersHandler" />
        <Buttons display="7" val="7" @click="numbersHandler" />
        <Buttons display="9" val="9" @click="numbersHandler" />
        <Buttons display="﹣" val="﹣" @click="minusHandler" />
      </div>
      <div class="rows">
        <Buttons display="4" val="4" @click="numbersHandler" />
        <Buttons display="5" val="5" @click="numbersHandler" />
        <Buttons display="6" val="6" @click="numbersHandler" />
        <Buttons display="÷" val="/" @click="divideHandler" />
      </div>
      <div class="rows">
        <Buttons display="1" val="1" @click="numbersHandler" />
        <Buttons display="2" val="2" @click="numbersHandler" />
        <Buttons display="3" val="3" @click="numbersHandler" />
        <Buttons display="x" val="*" @click="multiplyHandler" />
      </div>
      <div class="rows">
        <Buttons display="0" val="0" @click="numbersHandler" />
        <Buttons display="." val="." @click="numbersHandler" />
        <Buttons display="=" val="=" @click="equalHandler" />
        <Buttons display="+" val="+" @click="plusHandler" />
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
