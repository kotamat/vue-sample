<template xmlns:v-on="http://www.w3.org/1999/xhtml">
  <div>
    <input v-model="newTodo" @keyup.enter="addTodo">
    <ul>
      <li v-for="todo in todos">
        <div v-if="todo.text=='local'">local!</div>
        <span :class="{'white': $index%2==0, 'black': $index%2==1}">{{todo.text}}</span>
        <button @click="removeTodo($index)">X</button>
      </li>
    </ul>

  </div>
</template>
<style>
  .black{
    background-color: #000;
  }
  .white{
    background-color: #fff;
  }
</style>
<script>
  export default{
    data () {
      return {
        newTodo: '',
        todos: [
          {text: 'Add some todos'}
        ]
      }
    },
    methods: {
      addTodo: function () {
        var text = this.newTodo.trim()
        if (text) {
          this.todos.push({text: text})
          this.newTodo = ''
        }
      },
      removeTodo: function (index) {
        this.todos.splice(index, 1)
      }
    },
    computed: {
      b: function () {
        return this.todos + ['is todo']
      }
    }
  }
</script>
