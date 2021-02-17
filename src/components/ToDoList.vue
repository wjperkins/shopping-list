<template>
  <div class="todo-list">
    <h1>To-do list</h1>
    <input
      autofocus
      class="todo-input"
      v-model="newTodo.value"
      placeholder="Add a to-do..." 
      @keyup.enter="addTodo"
    />
    <ToDoItem
      v-for="(todo, index) in todos"
      :key="todo"
      :item="todo"
      @delete="deleteTodo(index)"
      @toggleComplete="toggleCompletedTodo(index)"
    />
  </div>
</template>

<script>
import ToDoItem from './ToDoItem.vue'

const blankTodo = { value: '', completed: false };

export default {
  components: { ToDoItem },
  name: 'ToDoList',
  data() {
    return {
      todos: [],
      newTodo: { ...blankTodo },
    }
  },
  methods: {
    addTodo() {
      if(this.newTodo.value.trim()) { 
        this.todos.unshift(this.newTodo);
        this.newTodo = { ...blankTodo };
        this.saveTodos();
      }
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
      this.saveTodos();
    },
    toggleCompletedTodo(index) {
      this.todos[index].completed = !(this.todos[index].completed);
      this.saveTodos();
    },
    loadTodos() {
      if(localStorage.getItem('todos')) {
        this.todos = JSON.parse(localStorage.getItem('todos'));
      }
    },
    saveTodos() {
      localStorage.setItem('todos', JSON.stringify(this.todos))
    }
  },
  mounted() {
    this.loadTodos();
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .todo-list {
    color: #eceff4;
    margin: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  .todo-input {
    padding: 10px;
    text-align: center;
    margin-bottom: 10px;
    border: none;
    border-radius: 5px;
    width: 400px;
    color: #2e3440;
    background: #d8dee9;
  }
</style>
