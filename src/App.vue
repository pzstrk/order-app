<template>
  <div id="app">
    <div class="container">
      <pizza-header></pizza-header>
    </div>
    <div class="container">
      <pizza-menu></pizza-menu>
    </div>
    <div class="container">

    </div>
  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue'
import Menu from './components/Menu.vue'

export default {
  name: 'app',
  components: {
    pizzaHeader: Header,
    pizzaMenu: Menu
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  /*color: #2c3e50;*/
  color: #292b2c;
  width: 100%;
}
</style>
