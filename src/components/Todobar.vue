<template>
<div id="todobar" >
<p>Что нужно сделать?</p>
<input type="text" class="form-control" id="todo-text" v-model="todos"  > 
<button class="btn " id="save-todo" @click="CreateTodo">СОХРАНИТЬ</button>
</div>
</template>
    
<script>
export default {
    props:['todochange'],
    data(){
        return{
            todos: this.todochange,
            shown:false
        }
    },
    methods:{
        CreateTodo(){
            this.$emit('CreateTodo',{todos:this.todos, shown:this.shown, todochange:this.todochange});
        }
    }
}
</script>

<style lang="scss">
#todobar{
    width: 500px;
    background: #FAFAFA;
    box-shadow: 0px 15px 12px rgba(0, 0, 0, 0.22), 0px 19px 38px rgba(0, 0, 0, 0.3);
    border-radius: 2px;
    height: 80vh;
    padding-left: 28px;
    padding-top: 25.44px;
}
@media screen  and (max-width: 900px){
    #todobar{
        width: 320px;
    }
}
#todo-text{
    width:90%;
    height: 44px;
    margin-bottom: 25px;
    ::-webkit-input-placeholder { color: rgba(31, 32, 65, 0.25); }
    ::-moz-placeholder          { color: rgba(31, 32, 65, 0.25); } 
    :-moz-placeholder           { color: rgba(31, 32, 65, 0.25); } 
    :-ms-input-placeholder      { color: rgba(31, 32, 65, 0.25); }
    }
#save-todo{
    background: #FFFFFF;
    border: 1px solid #DBDBDB;
    border-radius: 2px;
    font-weight: 500;
    font-size: 14px;
    line-height: 16px;
    text-align: center;
    letter-spacing: 0.0357143em;
    color: #BB6BD9;
    font-family: Montserrat;
    font-style: normal;
    font-weight: bold;
}
</style>