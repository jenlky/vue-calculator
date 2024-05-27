<script>
import Buttons from '../components/Buttons.vue'

export default {
  components: {
    Buttons
  },
  data() {
    return {
      result: 0
    }
  },
  methods: {
    numbers (value) {
      this.result = this.result.concat(value)
    }
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
        <Buttons val="CE" />
        <Buttons val="C" />
      </div>
      <div class="rows">
        <Buttons val="7" />
        <Buttons val="8" />
        <Buttons val="9" />
        <Buttons val="﹣" />
      </div>
      <div class="rows">
        <Buttons val="4" />
        <Buttons val="5" />
        <Buttons val="6" />
        <Buttons val="÷" />
      </div>
      <div class="rows">
        <Buttons val="1" />
        <Buttons val="2" />
        <Buttons val="3" />
        <Buttons val="x" />
      </div>
      <div class="rows">
        <Buttons val="0" />
        <Buttons val="." />
        <Buttons val="=" />
        <Buttons val="+" />
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
