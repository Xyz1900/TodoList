<template>
  <div>
    <ul>
      <div v-for="item in todos" :key="item.id">
        <MyItem          
          :todoObj="item" 
          :checkDone="checkDone"
          :deleteItem="deleteItem"
        />
      </div>
    </ul>
  </div>
</template>

<script>
  import MyItem from './MyItem'
  export default {
    name: 'MyList',
    props: ['todos','checkDone','deleteItem'],
    components:{MyItem}
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul{
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
