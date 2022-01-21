<template>
  <div id="app">
    <form v-on:submit.prevent="submitForm">
      <input id="todoText" type="text" v-model="todoText">
      <button type="submit">작성</button>
    </form>
    <ul>
      <li v-bind:id="'Todo'+todo.todoNum" v-for="todo in todos" :key="todo.content"  >
        <span v-if="!todo.complate">
          {{todo.content}}
          <button v-on:click="check(todo)">완료</button>
        </span>
        <span v-else-if="todo.complate"></span>
      </li>
    </ul>
    
    
  </div>
  
</template>

<script>
 
export default {

  data:function(){
    return{
      todoCount:0,
      todoText:'',
      todos: [],
    }
  },
  methods:{
    submitForm:function(){
      this.todoCount > 0 ? this.todoCount++ : this.todoCount = 1,
      this.todos.push({
        todoNum:this.todoCount,
        content:this.todoText,
        complate:false,
      })
      this.todoText = ''
    },
    check:function(todo){
      todo.complate = !todo.complate
    },
    }
  }
</script>

<style>
  ul{
    margin: 0;
    padding: 0;
  }
  li{
    list-style: none;
  }
</style>