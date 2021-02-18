<template>
  <div class="shopping-list">
    <h1>Shopping list</h1>
    <input
      autofocus
      class="item-input"
      v-model="newItem.value"
      placeholder="Add item" 
      @keyup.enter="addItem()"
    />
    <ListItem
      v-for="(item, index) in items"
      :key="item"
      :item="item"
      @delete="deleteItem(index)"
      @toggleComplete="toggleCompletedItem(index)"
    />
  </div>
</template>

<script>
import ListItem from './ListItem.vue'

const blankItem = { value: '', completed: false };

export default {
  components: { ListItem },
  name: 'ShoppingList',
  data() {
    return {
      items: [],
      newItem: { ...blankItem },
    }
  },
  methods: {
    addItem() {
      if(this.newItem.value.trim()) { 
        this.items.unshift(this.newItem);
        this.newItem = { ...blankItem };
        this.saveItems();
      }
    },
    deleteItem(index) {
      this.items.splice(index, 1);
      this.saveItems();
    },
    toggleCompletedItem(index) {
      this.items[index].completed = !(this.items[index].completed);
      this.saveItems();
    },
    loadItems() {
      if(localStorage.getItem('items')) {
        this.items = JSON.parse(localStorage.getItem('items'));
      }
    },
    saveItems() {
      localStorage.setItem('items', JSON.stringify(this.items))
    }
  },
  mounted() {
    this.loadItems();
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .shopping-list {
    color: #eceff4;
    margin: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 400px;
  }
  .item-input {
    padding: 10px;
    text-align: center;
    margin-bottom: 10px;
    border: none;
    border-radius: 5px;
    width: calc(100% - 20px);
    color: #2e3440;
    background: #d8dee9;
  }
  @media screen and (max-width: 500px) {
    .item-input {
      width: 300px;
    }
  }
</style>
