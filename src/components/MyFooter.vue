<template>
  <div v-show="todos.length" class="myFooter">
    <div class="myFooterContent">
      <div class="myFooterContentContent">
        <label>
          <!-- <input type="checkbox" :checked="isAll" @change="changeItemsDone"/> -->
          <input type="checkbox" v-model="isAll" />
        </label>
        <span>
          <span>已完成{{hasDoneCount}}</span> / 全部{{todos.length}}
        </span>
      </div>
      
    </div>
    <button @click="deleteDone">删除已完成任务</button>
  </div>
</template>

<script>
  export default {
    name: 'MyFooter',
    props: ['todos','deleteHasDone'],
    computed:{
      hasDoneCount(){
        let count=0
        this.todos.forEach(todo => {
           if(todo.done){count++}
        });
        return count
      },
      isAll:{
        get(){
          return this.hasDoneCount===this.todos.length && this.todos.length!==0
        },
        set(value){
            this.todos.forEach(todo => {
                todo.done=value
            });
        }
      }
    },
    methods:{
      deleteDone(){
        this.deleteHasDone()
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .myFooter{
    width: 100%;
    height: 25px;
    display: flex;
    justify-content: center;
  }
  button{
    width: 130px;
    display: none;
    position: absolute;
  }
  .myFooterContent{
    display: flex;
    flex-direction: row;
  }
  .myFooterContentContent{
    width: 300px;
    display: flex;
    justify-content: start;
  }
  .myFooter:hover button{
    display: block;
    margin-left: 260px;
  }
</style>
