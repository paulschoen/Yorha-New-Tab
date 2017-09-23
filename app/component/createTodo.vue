<template>
  <div>
    <p class="new-todo-text">New Todo</p>
    <div class="large-border">
      <div class="small-border">
        <img class="input-arrow" src="/images/arrow.png" alt='arrow'>
        <input type="text" class="todo-input" placeholder="Add New Todo" v-model='newTodo' @keyup.enter="addTodo">
      </div>
    </div>
  </div>
</template>

<script>
export default{
  methods:{
    addTodo: function(){
      alert(this.newTodo);
    }
  }

}
</script>

<style lang='css'>
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
