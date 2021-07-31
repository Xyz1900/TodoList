<template>
  <div id="app">
    <div class="allBorder">
      <MyHeader :addTodo="addTodo" :todos="todos"/>
      <MyList :todos="todos" :checkDone="checkDone" :deleteItem="deleteItem"/>
      <MyFooter :todos="todos" :deleteHasDone="deleteHasDone"/>
    </div>
  </div>
</template>

<script>
  import MyHeader from './components/MyHeader.vue'
  import MyList from './components/MyList.vue'
  import MyFooter from './components/MyFooter.vue'

  export default {
    name: 'App',
    data(){
      return{
       todos:JSON.parse(localStorage.getItem('todos')) || []
      }
    },
    methods:{

      addTodo(todoObj){
        this.todos.unshift(todoObj)
      },

      checkDone(todoId){
        this.todos.forEach((todo)=>{
          if(todo.id===todoId){
            todo.done=!todo.done
          }
        })
      },

      deleteItem(todoId){
        this.todos=this.todos.filter((todo)=>{
          return todo.id !== todoId
        })
      },
      deleteHasDone(){
        this.todos=this.todos.filter((todo)=>{
          return !todo.done
        })
      }
      
    },
    watch:{
      todos:{
        deep:true,
        handler(value){
          localStorage.setItem('todos',JSON.stringify(value))
        }
      }
    },
    components: {
      MyHeader,
      MyList,
      MyFooter
    }
  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  align-items: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
}
.allBorder{
  width: 90%;
  height: 100%;
  border-width: 1px;
  border-style: solid;
  border-color: gray;
}
button{
  width: 50px;
  height: 25px;
  background-color: red;
  border-radius: 5px;
  color: white;
  border-color: red;
}
</style>