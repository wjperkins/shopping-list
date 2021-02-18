<template>
  <div class="root">
    <ShoppingList />
  </div>
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
.root {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  padding-top: 60px;
  padding-bottom: 60px;
  display: flex;
  justify-content: center;
}
body {
  margin: 0px;
  background: #2e3440;
}
@media screen and (max-height: 800px) {
  .root {
    padding-top: 20px;
    padding-bottom: 20px;
  }
}
</style>
