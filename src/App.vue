<script>

export default {
    data() {
    return {
      todos: [
      ],
    }
  },
  methods: {
    addTodo() {
        if(this.newTodoText === ''){
            alert('INPUT YOUR TODO')
            return
        }
        this.todos.push({
            isDone: false,
            text: this.newTodoText,
        })
        this.newTodoText = ''
    },
    clearDoneTodos() {
        this.todos = this.todos.filter((todo) => !todo.isDone)
    },
  },
}
</script>

<template>
  <h1>My ToDo App</h1>
  <input type="text" v-model="newTodoText"/>
  <button @click="addTodo">追加</button>
  <button @click="clearDoneTodos">完了済みを削除する</button>
  <p v-if="(todos.length === 0)">ToDo is not set yet!</p>
  <ul v-else>
    <li v-for="(todo, index) in todos" v-bind:key="index">
      <input type="checkbox" v-model="todo.isDone" /><span :class="{ 'todo-done': todo.isDone }"
        >{{ todo.text }}</span
      >
    </li>

  </ul>
</template>

<style>
body {
  background-color: #eee;
}

.todo-done {
  text-decoration: line-through;
}
</style>