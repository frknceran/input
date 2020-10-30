<template>
  <div id="app">
    <StringInput
      v-model="value"
      :isNumber="true"
      :isEmpty="true"
    />
  </div>
</template>

<script>
import StringInput from './components/StringInput.vue'


export default {
  name: 'App',
  components: {
    StringInput
  },
  data() {
    return {
      value: ""
    }
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
