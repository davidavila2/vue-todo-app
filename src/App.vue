<template>
  <div>
    <input type="text" name="title" id="title" v-model="todo" placeholder="add todo...">
    <ul>
      <li v-for="todo in todos" v-bind:key="todo.id">{{todo.title}} <button v-on:click="deleteTodo(todo.id)">X</button></li>
    </ul>
    <div style="display: flex; flex-direction: row; justify-content: center; align-items: center;">
      <button style="width: 100px; margin-right: 10px;" @click="addTodo">Add Todo</button>
      <button style="width: 100px; margin-left: 10px" @click="resetTodos">Reset Todos</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      todo: '',
      todos: [
        {
          id: Math.random(),
          title: 'this is a todo',
        },
        {
          id: Math.random(),
          title: 'this is a todo too',
        },
      ],
      deleteTodo(id) {
        this.todos = this.todos.filter((todo) => todo.id !== id);
      },
      addTodo() {
        if(this.todo.length === 0) return;

        this.todos.push({ id: Math.random(), title: this.todo });
        this.todo = '';
      },
      resetTodos() {
        this.todos = [];
      }
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
