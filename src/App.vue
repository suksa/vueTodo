<template>
  <div id="app">
    <TodoHeader />
    <TodoInput v-on:dataInsert="dataInsertArr" />
    <TodoList v-bind:todos="todos"
      v-on:ckToggle="ckToggle"
      v-on:TodoDel="TodoDel"
       />
  </div>
</template>

<script>
  import TodoHeader from './components/TodoHeader.vue'
  import TodoInput from './components/TodoInput.vue'
  import TodoList from './components/TodoList.vue'

  export default {
    methods:{
      dataInsertArr(data){
        this.todos.push({
          id:this.id++,
          data,
          compleate:false
        })
      },
      ckToggle(index){
      this.todos[index].compleate = !this.todos[index].compleate
      },
      TodoDel(index){
        this.todos.splice(index,1)
      }
    },
    computed:{
      todos(){
        return this.$store.state.todos
      }
    },

    components:{
      TodoHeader,
      TodoInput,
      TodoList
    }
  }
</script>

<style scoped>

</style>