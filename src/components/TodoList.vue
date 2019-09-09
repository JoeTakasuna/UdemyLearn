<template lang="pug">
  .container
    h1 TODO List
    form(@submit.prevent)
      input(v-model="newItem" placeholder="ここに記入")
      v-btn(x-small @click="addItem") Add
    ul
      li(v-for="(todo, index) in todos")
        input(type="checkbox" v-model="todo.isDone")
        span(:class="{ done: todo.isDone }") {{ todo.item }}
        v-btn(x-small @click="deleteItem(index)") Delete
    pre {{ $data }}
</template>

<script>
export default {
  name: 'TodoList',
  data () {
    return {
      newItem: '',
      todos: []
    }
  },
  methods: {
    addItem: function() {
      if(this.newItem == '') return

      var todo = {
        item: this.newItem,
        isDone: false
      }
      this.todos.push(todo)
      this.newItem = ''
    },
    deleteItem: function(index) {
      this.todos.splice(index, 1)
    }
  }
};
</script>

<style scoped>
.container {
  margin: 24px;
}
ul {
  list-style: none;
}
li > span.done {
  text-decoration: line-through;
}
</style>
