<template>
  <div id="app">
    <DropDownList v-model="optionLabel" msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import DropDownList from './components/DropDownList.vue'

export default {
  name: 'app',
  data () {
    return {
      optionLabel: 1
    }
  },
  components: {
    DropDownList
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
