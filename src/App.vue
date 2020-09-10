<template>
  <div id="app" class="container">
    <div> 
      <h1>Список дел</h1>
      <p class="main-p">Добавляете и редактируйте списки дел</p>
      <ol style="padding-left: 10px; ">
        <li class=" todos-list" v-for="(todo,index) in todos" v-bind:key="todo.id">
          <div class="inner-li">  <p>{{ todo.text }}</p>
          <div style="margin:0px; padding: 0px;"> <button class="btn  change-el" @click="change(todo,index)" >Изменить</button>
          <button class=" btn btn-danger del-el" v-on:click ="removeElement(index)"> Удалить</button>
          </div>
          </div>

        </li>
      </ol>
      <button id="add-task" class="btn" @click="()=>{seen=!seen} ">Добавить дело</button>
    </div>
    <Todobar v-if="seen" @CreateTodo='onTodo'  :todochange = "this.val"  />
  </div>
</template>

<script>
import Todobar from "./components/Todobar"
export default {
  name: 'App',
  components: {
    Todobar
  },

  data(){
    return{
      seen:false,
      todos:[],
      val:this.val,
      key:0
    }
  },

  methods:{
    onTodo(data){
      if(data.todochange === undefined){

      this.todos.push({text:data.todos})

      }else {
          this.todos.filter(todo =>{
            todo.text = data.todochange
            todo.text = data.todos
            this.val= '';
            console.log(todo.text)
          })
      }

      this.seen = data.shown
    },

    removeElement(index){
        this.todos.splice(index,1)
    },

    change(index){
      this.seen=!this.seen
      this.val = index.text 
      }

  },
}
</script>

<style lang="scss">
@import 'node_modules/bootstrap/scss/bootstrap';
@import 'node_modules/bootstrap-vue/src/index.scss';

  #app{
    width: 100%;
    margin-top:4.1%;
    display: flex;
    justify-content: space-between;
  }
  
  h1{
    font-family: 'Open Sans', sans-serif;
    font-weight: 700;
    font-size: 48px;
    line-height: 60px;
    color: #1F2041;
  }

  .main-p{
    width: 320px;
    height: 20px;
    font-family: 'Open Sans', sans-serif;
    font-style: normal;
    font-weight: 700;
    font-size: 14px;
    line-height: 18px;
    margin-top: 10px;
    margin-bottom: 33px;
  }

  #add-task{
    margin-top: 10px;
    margin-bottom: 10px;
    height: 44px;
    background: #BB6BD9;
    border-radius: 22px;
    border-color: #BB6BD9;
    color: white;
    font-family: Montserrat;
    font-style: normal;
    font-weight: bold;
    font-size: 12px;
    line-height: 15px;
  }
  
  .todos-list{
    width: 500px;
    height: 35px;
    padding-bottom: 10px;
    border-bottom: 1px solid #CACACA;
    font-family: Montserrat;
    font-style: normal;
    font-weight: bold;
    font-size: 12px;
    line-height: 15px;
    margin-top: 10px;;
  }
 

.inner-li{
  display: flex;
  justify-content: space-between;
  align-items: center;
}
 .inner-li p{
   height:16px ;
   max-width: 200px;
    overflow:hidden;
 }
  .change-el{
    
    margin-left:30px;
    height: 33px;
    background: #BB6BD9;
    border-radius: 22px;
    border-color: #BB6BD9;
    color: white;
    font-family: Montserrat;
    font-style: normal;
    font-weight: bold;
    font-size: 12px;
    line-height: 15px;
    
  }
  .del-el{
    height: 33px;
    border-radius: 22px;
    font-family: Montserrat;
    font-style: normal;
    font-weight: bold;
    font-size: 12px;
    line-height: 15px;
    margin-left: 14px;
  }

  p{
    margin-bottom: 0px;
  }


  @media screen and (max-width: 1000px) {
    .todos-list{
      width: 320px;
    }
     .inner-li p{
        max-width: 100px;;
      }
  }

    @media screen  and (max-width: 767px){
     
    #app{
        flex-direction: column;
        align-items: center;
        justify-content: center;
    }
    ol{
      margin-right: 0px;
    }
}
</style>