<template>
  <div id="app">
    <h1>Список дел</h1>
    <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Что нужно сделать?">
    <button @click="addTodo">Добавить</button>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo }}
        <button @click="removeTodo(index)">Удалить</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTodo: '',
      todos: ['Изучить Vue', 'Сделать проект', 'Загрузить на GitHub']
    }
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push(this.newTodo);
        this.newTodo = '';
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    }
  }
}
</script>

<style>
#app { max-width: 400px; margin: 50px auto; font-family: sans-serif; }
li { margin-bottom: 10px; display: flex; justify-content: space-between; }
</style>