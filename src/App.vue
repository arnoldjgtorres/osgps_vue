<template>
  <div id="app">
    <!--
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    {{ todos }}
    -->
    <h2>Vue / Go Project</h2>
    <button v-on:click="accessAPI">Retrieve Data</button>
    <Display v-bind:content="content" />
  </div>
</template>

<script>
import Display from "./components/Display";
import axios from "axios";
//axios.defaults.headers.common["Access-Control-Allow-Origin"] = "*";
export default {
  name: "app",
  components: {
    //Todos,
    //AddTodo,
    Display
  },
  data() {
    return {
      todos: [],
      content: null
    };
  },
  methods: {
    /*
    deleteTodo(id) {
      axios
        .delete(`http://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res => (this.todos = this.todos.filter(todo => todo.id !== id)))
        .catch(err => console.log(err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;
      axios
        .post("http://jsonplaceholder.typicode.com/todos", {
          title,
          completed
        })
        .then(res => console.log(res.data))
        .catch(err => console.log(err));
    },*/
    accessAPI() {
      axios
        //.get("http://jsonplaceholder.typicode.com/todos?_limit=5")
        .get("https://osgps-server.herokuapp.com/")
        //.then(res => (this.todos = res.data))
        .then(res => {
          this.content = res.data;
          console.log(res);
        })
        .catch(err => console.log(err));
    }
  }
};
</script>

<style>
h2 {
  text-align: center;
}
button {
  margin-top: 2%;
}
</style>
