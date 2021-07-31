<template>
  <li>
      <label>
        <input type="checkbox" :checked="todoObj.done" @change="handlerCheck(todoObj.id)"/>
        <!-- <input type="checkbox" v-model="item.done"/> -->
        <span>{{todoObj.title}}</span>
      </label>
      <button @click="deleteItemById(todoObj.id)">删除</button>
  </li>
</template>

<script>
export default {
  name: 'MyItem',
  props:['todoObj','checkDone','deleteItem'],
  data(){
    return{

    }
  },
  methods:{
    handlerCheck(id){
      this.checkDone(id)
    },
    deleteItemById(id){
      this.deleteItem(id)
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  label{
    float: left;
  }
  li{
    list-style: none;
    width: 300px;
    height: 25px;
    border-width: 1px;
    border-style: solid;
    border-color: #ddd;
  }
  li:hover{
    background-color: #ddd;
  }
  /* div div{
    display: flex;
    justify-content: center;
  } */
  button{
    display: none;
  }
  span{
    margin-left: 5px;
  }
  li:hover button{
    display: block;
    float: right;
  }
</style>
