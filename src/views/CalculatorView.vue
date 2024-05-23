<script setup lang="ts">
import Buttons from '../components/Buttons.vue'
</script>

<template>
  <div class="calculator">
    <div class="results">
      <span>123</span>
    </div>
    <div class="calculator-btns">
      <div class="rows">
        <Buttons val="7" />
        <Buttons val="8" />
        <Buttons val="9" />
        <Buttons val="-" />
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
  background-color: green;
  min-height: 60vh;
  align-items: center;
}

.rows {
  display: flex;
}

.results {
  span {

  }
}

.calculator-btns {
  margin: 30px 15px;
}
</style>
