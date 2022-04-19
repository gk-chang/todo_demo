<template>
    <div class="todo-list">
        <todo-list-item v-for="n in 3" :key="n"></todo-list-item>
    </div>
</template>

<script>
import TodoListItem from './TodoListItem';
export default {
    components: { TodoListItem },
    name:"TodoList",

}
</script>

<style>
.todo-list {
  display:grid;
  row-gap:14px;
}

</style>