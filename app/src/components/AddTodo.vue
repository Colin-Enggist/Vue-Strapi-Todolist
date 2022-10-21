<template>
    <div class="cont">
        <div ref="temp" class="todoCard">
            <button v-on:click="save" class="save">
                <span>add</span>
            </button>
            <input ref="date" class="Day" type="date"/>
            <input ref="title" class="Title" type="text" placeholder="Title"/>
            <textarea ref="desc" class="Descr" placeholder="Describtion"></textarea>
        </div>
    <button v-on:click="toggle()" class="add">
        <span>New Todo</span>
    </button>
    
    </div>
</template>

<script>
export default{
    name: "AddTodo",
    props:{
        post:Function,
    },
    data(){
        return{
            compute:{
                data:{
                    Day: Date,
                    Name: String,
                   Describtion: String
                }
            }
        }
    },
    methods:{
        toggle(){
            switch(this.$refs.temp.style.display){
                case "none":
                this.$refs.temp.style.display = "block";
                break;
                default:
                this.$refs.temp.style.display="none"
                break;
            }
        },
        
        save(){
            this.compute= {
                    data:{
                        Day: this.$refs.date.value,
                        Name: this.$refs.title.value,
                        Describtion: this.$refs.desc.value
                    }
                    }
            this.$refs.date.value= null;
            this.$refs.title.value= null;
            this.$refs.desc.value=null;
            this.toggle();
            this.post(this.compute);
            this.compute= {
                    data:{
                        Day: null,
                        Name: null,
                        Describtion: null
                    }
                 }    
        }
    },
    mounted(){
        this.$refs.temp.style.display="none"
    }

}
</script>

<style>
.cont{
    position: absolute;
    right: 0px;
    bottom: 0px;
    display: flex;
    flex-direction: column;
}
.add{
    width: 310px;
    height: 80px;
    background-color: greenyellow;
}
.add span{
    font-size: 20px;
}
.temp{
    display:none;
}
.save{
    position: absolute;
    right: 0px;
    border-top-right-radius: 30px;
    border-color: yellowgreen;
    width: 70px;
    height: 18%;
    background-color: greenyellow;
    z-index: 1;
}
.save span{
    font-size: 15px;
}
.Day{
    height: 18%;
    width: 85%;
    position: absolute;
    left: 0px;
    border-top-left-radius: 30px;
    font-size: 25px;
    border: none;
    padding-left: 20px;
    border-bottom: 2px solid black;
}
.Title{
    position: absolute;
    top: 18%;
    width: 100%;
    padding-left: 20px;
    left: 0px;
    border: none;
    background-color: transparent;
    font-size: 30px;
    margin-top: 30px;
}
.Descr{
    position: absolute;
    bottom: 0px;
    width: 100%;
    left: 0px;
    border-bottom-left-radius: 30px;
    border-bottom-right-radius: 30px;
    background-color: transparent;
    height: 52%;
    font-size: 20px;
    border: none;
    padding: 20px;
}
</style>