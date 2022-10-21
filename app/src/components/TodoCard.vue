<template>
    <div class="todoCard">
        <button v-on:click="del" class="delete">
            <span>DEL</span>
        </button>
        <h2>{{date}}</h2>
        <div class="content">
            <h1>{{title}}</h1>
            <p>{{describtion}}</p>
        </div>
    </div>
    
</template>

<script>

export default{
    name: "TodoCard",
    props:{
        todo: [],
        call: Function,
    },
    data(){
        return{
            date: this.todo.attributes.Day,
            title: this.todo.attributes.Name,
            describtion: this.todo.attributes.Describtion,
            id: this.todo.id
        }
    },
    methods:{
        del(){
            var url = "http://localhost:1337/api/todos/" + this.todo.id;
            this.call(url)
        }
    }
}
</script>

<style>
.todoCard{
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
.delete{
    position: absolute;
    right: 0px;
    top: 0px;
    border-top-right-radius: 30px;
    width: 70px;
    height: 18%;
    background-color: lightcoral;
}
</style>