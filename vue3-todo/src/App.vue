<template>
  <TodoHeader></TodoHeader>
  <TodoInput
    @addItem="addItem">
  </TodoInput>
  <TodoList
    :todoList="todoItems">
  </TodoList>
  <TodoFooter></TodoFooter>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  components: {
    TodoHeader,
    TodoInput,
    TodoList,
    TodoFooter,
  },
  data() {
    return {
      todoItems: []
    }
  },
  methods: {
    addItem(value) {
      this.todoItems.push(value);
      localStorage.setItem(value, value);
    }
  }
}
</script>

<style>

</style>
