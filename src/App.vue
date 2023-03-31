<template>
  <div id="app">
    <h1>To Do List</h1>
    <to-do-form @todo-added="addToDo"></to-do-form>
    <ul>
      <li v-for="item in ToDoItems" :key="item.id">
        <to-do-item :label="item.label" :done="item.done" :id="item.id"></to-do-item>
      </li>
    </ul>
  </div>

  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import ToDoItem from "./components/ToDoItem.vue";
import uniqueId from "lodash.uniqueid";
import ToDoForm from "./components/ToDoForm.vue";



export default {
  name: 'app',
  components: {
    ToDoItem,
    ToDoForm
  },
  data(){
    return{
      ToDoItems:[
        {id:uniqueId("todo-"),label:"Learn Vue",done:false},
        {id:uniqueId("todo-"),label:"Start VUE CLI",done:true},
        {id:uniqueId("todo-"),label:"Make component",done:true},
        {id:uniqueId("todo-"),label:"Render list of components",done:false},
      ]
    }
  },
  methods:{
    addToDo(toDoLabel){
      // console.log("New To Do Added is ", toDoLabel);
      this.ToDoItems.push({id:uniqueId("todo-"),label:toDoLabel,done:false});
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
