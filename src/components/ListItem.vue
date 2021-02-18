<template>
  <div class="item" @click="toggleCompletedItem()">
    <div :class="{ completed: item.completed }">
      {{item.value}}
    </div>
    <button @click.stop="deleteItem()" class="delete-btn">
      Delete
    </button>
  </div>
</template>

<script>
export default {
  name: 'ListItem',
  props: {
    item: { value: String, completed: Boolean }
  },
  emits: ['delete', 'toggleComplete'],
  methods: {
    deleteItem() {
      this.$emit('delete')
    },
    toggleCompletedItem() {
      this.$emit('toggleComplete')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .item {
    color: #2e3440;
    background: #88c0d0;
    padding: 10px;
    margin: 10px;
    width: calc(100% - 20px);
    border-radius: 5px;
    word-break: break-all;
    display: flex;
    justify-content: space-between;
    align-items: center;
    cursor: pointer;
  }
  .item .completed {
    text-decoration: line-through;
  }
  .item .delete-btn {
    color: #2e3440;
    background: #d8dee9;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    flex-shrink: 0;
    margin-left: 5px;
    padding: 5px;
  }
  @media screen and (max-width: 500px) {
    .item {
      width: 300px;
    }
  }
</style>
