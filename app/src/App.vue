<template> 
<div class="wrapper">
  <AddTodo :post="postCard"/>
  <TodoCard v-for="(todo, index) in todos" :key="index" :todo="todo" :call="delEntry"/>
</div>
</template>

<script>


import TodoCard from "./components/TodoCard"
import AddTodo from "./components/AddTodo.vue"
export default {
  name: 'App',
  components: {
    TodoCard,
    AddTodo
  },

  data() {
    return{
      todos: [],
    };
  },
  methods:{
    postCard(compute){
            fetch("http://localhost:1337/api/todos/",{
                method: "POST",
                headers: {
                    'Content-Type': 'application/json'
                },
                body: JSON.stringify(compute)
            }).then(this.getData())
        },

    getData(){
      fetch("http://localhost:1337/api/todos/", {
      method: "GET",
      headers: {
        'Content-Type': 'application/json'
      },
      }).then((response)=>response.json(response.body))
        .then((data)=> this.todos=data.data);
    },
    delEntry(url){
      fetch(url,{
        method: "DELETE",
        headers: {
        'Content-Type': 'application/json'
      },
      }).then(this.getData())
    }
  },

  mounted() {
      this.getData()
    },
}
</script>

<style>
html{
  background-color: lightgray;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
}
.wrapper{
  width: 80%;
  height: 92vh;
  overflow: scroll;
  margin: 0 auto;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  background-color: white;
  overflow-y: hidden; /* Hide vertical scrollbar */
  overflow-x: hidden; /* Hide horizontal scrollbar */
  justify-content: space-around;
  position: relative;
}
</style>
