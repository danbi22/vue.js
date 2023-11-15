<template>
  <div class="inputBox shadow">
    <input type="text" placeholder="할 일을 입력하세요." v-model="todoItem" @keyup.enter="addTodo">
    <span class="addContainer" @click="addTodo">
      <i class="addBtn fas fa-plus" aria-hidden="true"></i>
    </span>
  </div>
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
          console.log(this.todoItem);
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
    input:focus {
    outline: none;
  }
  .inputBox {
    background: white;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
  }
  .inputBox input {
    border-style: none;
    font-size: 0.9rem;
  }
  .addContainer {
    float: right;
    background: linear-gradient(to right, #6478FB, #8763FB);
    display: block;
    width: 3rem;
    border-radius: 0 5px 5px 0;
  }
  .addBtn {
    color: white;
    vertical-align: middle;
  }
</style>