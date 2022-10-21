<template>
    <div class="todolist">
        <h2>{{date}}</h2>
        <div class="content">
            <h1>{{todoName}}</h1>
            <p>{{todoDescribtion}}</p>
        </div>
    </div>
    
</template>

<script>

export default{
    name: "TodoCard",
    props:{
        date: String,
        todoName: String,
        todoDescribtion: String,
    },
}
</script>

<style>
.todolist{
    width: 300px;
    height: 400px;
    border: 5px solid black;
    border-radius: 30px;
    position: relative;
    margin-top: 18px;
}
h2{
    position: absolute;
    top: 10px;
    left: 20px;
}
.content{
    width: 100%;
    height: 82%;
    position: absolute;
    bottom: 0;
    border-bottom-right-radius: 30px;
    border-bottom-left-radius: 30px;
    border-top: 2px solid black;
    display: flex;
    flex-direction: column;
    text-align: left;
    overflow: scroll;
    overflow-y: hidden; /* Hide vertical scrollbar */
  overflow-x: hidden; /* Hide horizontal scrollbar */
}

h1{
    margin-left: 20px;
}

p{
    margin-left: 25px;
    font-size: 20px;
    margin-top: 0;
}
</style>