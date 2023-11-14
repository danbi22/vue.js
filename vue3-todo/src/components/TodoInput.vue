<template>
  <input type="text" placeholder="할 일을 입력하세요." v-model="todoItem" @keyup.enter="addTodo">
  <button @click="addTodo">+</button>
</template>

<script>
  export default {
    data() {
      return {
        todoItem: ''
      }
    },
    methods: {
      addTodo() {
        if (this.todoItem !== '') {
          this.$emit('addItem', this.todoItem);
          this.clearInput();
        }
      },
      clearInput() {
        this.todoItem = '';
      }
    }
  }
</script>

<style scoped>

</style>