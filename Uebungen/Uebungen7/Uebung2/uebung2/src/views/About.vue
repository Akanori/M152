<template>
  <div class="content">
    {{ myString }}
    <br>
    <input type="text" v-model="myString" />
    <br><br>
    <h1>{{todos.length}} Aufgaben für heute</h1>
    <br>
    <h3>{{totalTime}} Minuten total</h3>
    <ul>
      <li v-for="todo in todos">{{todo.name}} ({{todo.time}})}}</li>
    </ul>

    <input v-model="newTodo" />
    <input v-model="newTime" />
    <button v-on:click="addTodo()">Eintrag hinzufügen</button>
  </div>
</template>

<script>

export default {
  name: 'App',
  data: function(){
    return{
      myString: 'Hello World2',
      todos: [
        {
          name: 'eins',
          time: 45
        },
        {
          name: 'zwei',
          time: 45
        },
        {
          name: 'drei',
          time: 45
        }
      ],
      newTodo: "",
      newTime: 0
    }
  },
  methods: {
    addTodo: function(){
      this.todos.push({
        name: this.newTodo,
        time: this.newTime
      });
      this.newTodo = '';
    }
  },
  computed: {
    todocount: function(){
      return this.todos.length;
    },
    totalTime: function(){
      var time = 0;

      this.todos.forEach(todo => {
        time += parseInt(todo.time);
      });

      return time;
    }
  }
}
</script>


<style lang="scss">

.content{
  width: 800px;
  margin: 0 auto;
}
</style>