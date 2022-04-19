<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  <main>
    <div class="container">
      <h1>欢迎使用</h1>
      <!-- <todo-add></todo-add> -->
      <todo-add :tid="todos.length" @add-todo="addTodo" />
      <todo-filer :selected="filter" @change-filter="filter = $event" />
      <todo-list :todos="filteredTodos" />
    </div>
  </main>
</template>

<script>
// import { ref, computed } from 'vue';
import TodoAdd from './components/TodoAdd.vue'
import TodoFiler from './components/TodoFiler.vue'
import TodoList from './components/TodoList.vue'
import useTodos from "./components/composables/useTodos.js";
import useFilteredTodos from "./components/composables/useFilteredTodos.js";
// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    TodoAdd,
    TodoFiler,
    TodoList
    // HelloWorld
  },
  setup() {
    const {todos, addTodo} = useTodos();
    const {filter, filteredTodos} = useFilteredTodos(todos);

    return {
      todos,
      addTodo,
      filter,
      filteredTodos,
    }
    
  }
}
</script>

<style>
* {
  box-sizing:border-box;
  margin:0;
  padding:0;
  font-family: Helvetica, "gengsha", "Microsoft Yahei", sans-serif
}

img {
  width:50;
  display: none;
}

/*整个页面*/
main
{
  width: 100vw;
  min-height: 100vh;
  display: grid;
  align-items: center;
  justify-items: center;
  background: rgb(203, 210, 240);
  }

.container {
  width: 60%;
  max-width: 400px;
  box-shadow: 0px 0px 24px rgba(0, 0, 0, 0.15);
  border-radius: 24px;
  padding: 48px 28px;
  background-color: rgb(245, 246, 252);
}

h1 {
  margin:24px 0;
  font-size: 28px;
  color: #414873;
}


</style>
