<template>
  <div id="app">
    <h3>Todo list</h3>
    <hr>
    <TodoList
            v-bind:todos="todos"
            v-on:remove="removeTodo"
    />
    <AddTodo
            v-on:add-todo="addTodo"
    />
  </div>
</template>

<script>
  import TodoList from "@/components/TodoList";
  import AddTodo from "@/components/AddTodo";

  export default {
    name: 'app',
    components: {
      TodoList,
      AddTodo
    },
    data(){
      return{
        todos: [
          {id: 1, title: "Купить хлеб", completed: false},
          {id: 2, title: "Купить воду", completed: false},
          {id: 3, title: "Купить молоко", completed: false},
        ]
      }
    },
    methods:{
      removeTodo: function (id) {
        this.todos = this.todos.filter(todo => todo.id !== id)
      },
      addTodo: function (todo) {
        this.todos.push(todo);
      }
    }
  }
</script>

<style lang="less">
  #app{
    .todo-list{
      max-width: 400px;
      width: 100%;
      display: flex;
      flex-direction: column;
      &__item{
        display: flex;
        width: 100%;
        justify-content: space-between;
        margin: 5px 0;
        &.completed{
          text-decoration: line-through;
        }
      }
    }
  }
</style>
