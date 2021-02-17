<template>
  <div class="item">
    <input
      type="checkbox"
      :checked="item.completed"
      @input="toggleCompletedTodo"
    />
    <div :class="{ completed: item.completed }">
      {{item.value}}
    </div>
    <button @click="deleteTodo" class="delete-btn">
      Delete
    </button>
  </div>
</template>

<script>
export default {
  name: 'ToDoItem',
  props: {
    item: { value: String, completed: Boolean }
  },
  emits: ['delete', 'toggleComplete'],
  methods: {
    deleteTodo() {
      this.$emit('delete')
    },
    toggleCompletedTodo() {
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
    width: 400px;
    border-radius: 5px;
    word-break: break-all;
    display: flex;
    justify-content: space-between;
    align-items: center;
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
</style>
