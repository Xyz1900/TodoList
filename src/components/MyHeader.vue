<template>
  <div>
    <input type="text" placeholder="请输入需要完成的任务，按下回车确认" v-model="title" @keydown.enter="duplicateCheckAdd"/>
  </div>
</template>

<script>
  import {nanoid} from 'nanoid'
  export default {
    name: 'MyHeader',
    props: ['addTodo','todos'],
    data(){
      return{
        title:''
      }
    },
    methods:{
      // add(){
      //   if(this.title.trim()){
      //         const todoObj={id:nanoid(),title:this.title,done:false};
      //         this.addTodo(todoObj);
      //         this.title=''
      //       }else{
      //         alert('添加失败，输入不能为空')
      //       }
      // },
      duplicateCheckAdd(){
        let temp=true
        if(!this.title.trim()){
            alert('添加失败，输入不能为空');
            temp=false
          }else{
            this.todos.forEach(todo => {
              if(todo.title===this.title){
                alert('该任务已存在')
                temp=false
              }
            })
        }
        if(temp){
          const todoObj={id:nanoid(),title:this.title,done:false};
          this.addTodo(todoObj);
        }
        this.title=null
      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input{
  margin-top: 10px;
  width: 248px;
}

</style>
