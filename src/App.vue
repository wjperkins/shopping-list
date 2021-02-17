<template>
  <ShoppingList />
</template>

<script>
import ShoppingList from './components/ShoppingList';

export default {
  name: 'App',
  components: {
    ShoppingList
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  padding-top: 60px;
  padding-bottom: 60px;
}
body {
  margin: 0px;
  background: #2e3440;
}
</style>
