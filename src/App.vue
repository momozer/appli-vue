<!-- eslint-disable vue/require-v-for-key -->
<template>
 <HeaderVue/>
  <div class="todoList">
  <h1>{{ title }}</h1>
  <div v-if="!isEditing">
  <input @keyup.enter="HandleClick" type="text" v-model="todo">
  <input type="submit" value="Ajouter" @click="HandleClick">
</div>

  <div v-else>
  <input type="text" @keyup.enter="HandleClick" v-model="todo">
  <input type="submit" value="Update" @click="updateTodo">
</div>

  <div>
    <h3>Ma liste :</h3>
    <ol>
      <li  v-for="(todo, index) of todos" :key="index">
        {{ todo }} 
        <button @click="editTodo(index, todo)">Modifier</button>
        <button @click="deleteTodo(index)">Supprimer</button>
        <select name="urgence" id="urgence">
          <option value="ttu">Trés urgent</option>
          <option value="u">Urgent</option>
          <option value="nonUrgent">Non urgent</option>
        </select>
      </li>
    </ol>
  </div>
</div>

<inscription-user/>

  

   
  
</template>

<script>
import InscriptionUser from './components/Inscription-user.vue';
import HeaderVue from './components/Header-component.vue';

export default {
  name: 'App',
  components:{
    InscriptionUser,
    HeaderVue
  },
   data(){
    return{
      isEditing : false,
      title : "Ma première application en Vue.js",
      todos : ["got to te market"],
      todo :"",
      selectedIndex : null,
       }
  },
  methods:{
    HandleClick(){      
      this.todos.push(this.todo);
      this.todo = "";
    },
    editTodo(index, todo){
      this.todo = todo;
      this.selectedIndex = index;
      this.isEditing = true;

    },
    deleteTodo(index){
      this.todos.splice(index, 1);

    },
    updateTodo(){
      this.todos.splice(this.selectedIndex, 1, this.todo);
      this.isEditing =false;
      this.todo="";
    }
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
h1{
  color: blueviolet;
  font-size: 4rem;
}
</style>
