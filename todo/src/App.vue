<template>
  <h1>ToDo App</h1>
  <form @submit.prevent="addToDo()">
    <label>New ToDo</label>
    <input type="text" v-model="content" />
    <button>Add ToDo</button>
    <h2>ToDo List ({{ todos.length }})</h2>
  </form>
  <ul>
    <li v-for="(todo, index) in todos" :key="index">
      <span
        :class="{ done: todo.done, notDone: !todo.done }"
        @click="doIt(todo)"
        >{{ todo.content }}</span
      ><button @click="removeToDo(index)">X</button>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'App',
  data () {
    return {
      todos: [
        { content: 'กินข้าว', done: false },
        { content: 'อ่านหนังสือ', done: true }
      ],
      content: ''
    }
  },
  methods: {
    addToDo () {
      console.log(this.content)
      this.todos.push({ content: this.content, done: false })
      this.content = ''
    },
    removeToDo (index) {
      console.log(index)
      this.todos.splice(index, 1)
    },
    doIt (todo) {
      todo.done = !todo.done
      console.log(todo)
    }
  }
}
</script>

<style>
.done {
  color: grey;
  text-decoration: line-through;
}
.notDone {
  color: blue;
}
</style>
