<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <div class="container">
    <label>Eleva a su propia potencia:  </label>
    <input type="number" v-model="inputValue" @keypress.enter="add">
  </div>
  <label>Personaliza la potencia:  </label>
  <input type="number" v-model="inputPowerValue" @keypress.enter="power">
  <Counter title="Counter 1" :start="startValue" :power="powerValue" @update-input-value="updateInputValue" />
</template>

<script>
import Counter from './components/Counter.vue'
export default {
  name: 'App',
  components: {
    Counter
  },
  data() {
    return {
      startValue: 1,
      inputValue: 1,
      inputPowerValue: 1,
      powerValue: null
    }
  },
  methods: {
    add() {
      this.startValue = this.inputValue
      this.powerValue = null;
    },
    power() {
      this.powerValue = this.inputPowerValue
    },
    updateInputValue(newVal) {
      this.inputValue = newVal
    }
  }
}
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

input {
  border: 2px solid #5aa67b,
}
</style>
