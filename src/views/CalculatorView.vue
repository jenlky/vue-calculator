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
      display: "0",
      result: "0"
    }
  },
  methods: {
    numbersHandler (e) {
      const value = e.currentTarget.textContent
      if (this.display === "0" && value !== ".") {
        this.display = value
        this.result = value
      } else {
        this.display = this.display + value
        this.result = this.result + value
      }
    },
    clearHandler () {
      this.display = "0"
      this.result = "0"
    },
    clearEntryHandler () {
      if (this.display.length > 0) {
        const values = this.display.split('')
        values.splice(-1, 1)
        this.display = values.join('') || "0"
      }
    },
    lastCharIsNotOperator () {
      return !regex.test(this.display[this.display.length-2])
    },
    plusHandler () {
      if (this.lastCharIsNotOperator()) {
        this.display = this.result + " + "
        this.result = this.display
      }
    },
    minusHandler () {
      if (this.lastCharIsNotOperator()) {
        this.display = this.result + " - "
        this.result = this.display
      }
    },
    multiplyHandler () {
      if (this.lastCharIsNotOperator()) {
        this.display = this.result + " x "
        this.result = this.result + " * "
      }
    },
    divideHandler () {
      if (this.lastCharIsNotOperator()) {
        this.display = this.result + " ÷ "
        this.result = this.result + " / "
      }
    },
    // sqRootHandler () {
    //   if (this.lastCharIsNotOperator()) {
    //     this.result = this.result + " √ "
    //   }
    // },
    equalHandler () {
      // const values = this.result.split(' ')
      // console.log('values', values)
      // console.log('add', this.mathLogic()["+"](3, 4))

      // values.map(val => {
        
      // })

      try {    
        this.result = eval(this.result)
        this.display = this.result
      } catch (error) {
        alert("Incorrect formatting")
      }
    },
    // to replace eval bc eval is not secure and you never know if the code you execute can be trusted
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
      <span>{{ display }}</span>
    </div>
    <div class="calculator-btns">
      <div class="rows special-symbols">
        <Buttons display="%" style="visibility: hidden;" />
        <Buttons display="√" @click="sqRootHandler" style="visibility: hidden;" />
        <Buttons display="CE" @click="clearEntryHandler" />
        <Buttons display="C" @click="clearHandler" />
      </div>
      <div class="rows">
        <Buttons display="8" @click="numbersHandler" />
        <Buttons display="7" @click="numbersHandler" />
        <Buttons display="9" @click="numbersHandler" />
        <Buttons display="﹣" @click="minusHandler" />
      </div>
      <div class="rows">
        <Buttons display="4" @click="numbersHandler" />
        <Buttons display="5" @click="numbersHandler" />
        <Buttons display="6" @click="numbersHandler" />
        <Buttons display="÷" @click="divideHandler" />
      </div>
      <div class="rows">
        <Buttons display="1" @click="numbersHandler" />
        <Buttons display="2" @click="numbersHandler" />
        <Buttons display="3" @click="numbersHandler" />
        <Buttons display="x" @click="multiplyHandler" />
      </div>
      <div class="rows">
        <Buttons display="0" @click="numbersHandler" />
        <Buttons display="." @click="numbersHandler" />
        <Buttons display="=" @click="equalHandler" />
        <Buttons display="+" @click="plusHandler" />
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
</style>
