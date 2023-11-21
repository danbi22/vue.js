<template>
  <div class="inputBox shadow">
    <input type="text" placeholder="할 일을 입력하세요." v-model="todoItem" @keyup.enter="addTodo">
    <span class="addContainer" @click="addTodo">
      <i class="addBtn fas fa-plus" aria-hidden="true"></i>
    </span>
    <AlertModal v-if="showModal" @close="showModal = false">
        <!--
      you can use custom content here to overwrite
      default content
    -->
      <template v-slot:header>경고</template>
      <template v-slot:body>할 일의 이름을 입력해주세요.</template>
    </AlertModal>
  </div>
</template>

<script>
  import AlertModal from './common/AlertModal.vue'

  export default {
    data() {
      return {
        todoItem: '',
        showModal: false
      }
    },
    methods: {
      addTodo() {
        if (this.todoItem !== '') {
          this.$emit('addItem', this.todoItem);
          console.log(this.todoItem);
          this.clearInput();
        } else {
          this.showModal = !this.showModal;
        }
      },
      clearInput() {
        this.todoItem = '';
      }
    },
    components: {
      AlertModal
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