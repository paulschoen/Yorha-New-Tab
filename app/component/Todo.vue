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
      <div>
        <p class="new-todo-text">New Todo</p>
        <div class="large-border">
          <div class="small-border">
            <img class="input-arrow" src="/images/arrow.png" alt='arrow'>
            <input type="text" class="todo-input" placeholder="Add New Todo" v-model='newTodo' @keyup.enter="addTodo">
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import $ from 'jquery';

export default {
  data(){
    return {
      renderCreateTodo: true,
      todos: '',
      square: '■',
      newTodo: '',
      todos: ''
    }
  },
  methods:{
    onload: function(){
      this.todos = JSON.parse(localStorage.getItem("todos"));
    },
    updateTodo: function(todo){
      this.todos.push(todo)
    },
    addTodo: function(){
      var value = this.newTodo
      if (!value){
        return
      }
      var id = Date.now()
      var todos = []
      var todo ={
        id: id,
        name: value,
        edit: false
      }
      if(!this.todos){
        todos.push(todo)
        localStorage.setItem("todos", JSON.stringify(todos));
      }else{
        this.todos.push(todo)
        localStorage.setItem("todos", JSON.stringify(this.todos));
        this.newTodo = ''
      }
      $('.todo-figure').append(
      '<div style="padding: 0" class="fadeInLeft">\n'+
        '<button style="margin-top: 0px;" type="button" class="custom-button">\n'+
          '<p><span>&#9632</span>'+todo.name+'</p>\n'+
          '<img class="arrow animated fadeIn" src="/images/arrow.png" alt="arrow">\n'+
        '</button>\n'+
      '</div>')
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
.new-todo-text{
  font-size: 17px;
  margin-bottom: 5px;
}
.input-arrow{
  position: absolute;
  height: 30px;
  margin-left:-20px;
}
.todo-input{
  margin-left: 20px;
  width: 87%;
  box-shadow: 3px 3px 5px #888888;
}
</style>
