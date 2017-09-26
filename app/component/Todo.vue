<template lang="html">
  <div class="todo-box">
    <div class="large-border">
      <div class="small-border">
        <figure class="todo-figure">
          <figcaption><span>&#9632</span> Listed Todos<span v-on:click="renderCreateTodo ? renderCreateTodo = false : renderCreateTodo = true" class="add-todo-button">+</span></figcaption>
          <div style="padding: 0" v-if="todos" v-for="todo in todos" class="fadeInLeft display-none">
            <button style="margin-top: 0px;" type="button" class="custom-button">
              <p>{{square+todo.name}}</p>
              <img class="arrow animated fadeIn" src="/images/arrow.png" alt="arrow">
            </button>
          </div>
        </figure>
      </div>
    </div>
    <div v-if="renderCreateTodo" class="animated fadeIn">
      <CreateTodo v-on:update="onload"></CreateTodo>
    </div>
  </div>
</template>

<script>
import CreateTodo from './createTodo.vue'

export default {
  data(){
    return {
      renderCreateTodo: true,
      todos: '',
      square: '■'
    }
  },
  components:{
    CreateTodo: CreateTodo,
  },
  // watch:{
  //   todos: function(){
  //     this.todos = JSON.parse(localStorage.getItem("todos"));
  //   }
  // },
  // events:{
  //   update: function(){
  //     this.todos = JSON.parse(localStorage.getItem("todos"));
  //     alert('update')
  //   }
  // },
  methods:{
    onload: function(){
      this.todos = JSON.parse(localStorage.getItem("todos"));
    }
  },
  beforeMount(){
    this.onload()
  }
}
</script>

<style lang="css">
.grid .todo-box{
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 25px;
}
.add-todo-button{
  float:right;
  font-weight: bold;
  font-size: 27px;
  background-color: #454138;
  cursor: pointer;
}
</style>
