<template lang="html">
  <div class="todo-box">
    <div class="large-border">
      <div class="small-border">
        <figure class="todo-figure">
          <figcaption><span>&#9632</span> Listed Todos<span v-on:click="renderCreateTodo ? renderCreateTodo = false : renderCreateTodo = true" class="add-todo-button">+</span></figcaption>
        </figure>
      </div>
    </div>
    <div v-if="renderCreateTodo" class="animated fadeIn">
      <CreateTodo></CreateTodo>
    </div>
  </div>
</template>

<script>
import CreateTodo from './createTodo.vue'

export default {
  data(){
    return {
      renderCreateTodo: true
    }
  },
  components:{
    CreateTodo: CreateTodo
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
