<template> 
<div class="wrapper">
  <TodoCard v-for="items in items" :key="items.key"/>
</div>
</template>

<script>

import TodoCard from "./components/TodoCard"

export default {
  name: 'App',
  components: {
    TodoCard
  },
  methods:{
    getPost(){
      fetch('http://localhost:1337/api/todos',{
        method: 'GET',
      })
      .then((response)=>response.json())
      .then(data=>{return data.data})
      .catch((error)=>console.log(error))
    }
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
}
</style>
