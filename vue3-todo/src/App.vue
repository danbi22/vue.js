<template>
  <TodoHeader></TodoHeader>
  <TodoInput
    @addItem="addItem">
  </TodoInput>
  <TodoList
    :todoList="todoItems"
    @removeItem="removeItem">
  </TodoList>
  <TodoFooter @clearAll="refresh"></TodoFooter>
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
      var obj = {completed: false, name: value}
      this.todoItems.push(obj);
      localStorage.setItem(value, JSON.stringify(obj));
    },
    removeItem(item, index) {
      localStorage.removeItem(item);
      this.todoItems.splice(index, 1);
    },
    refresh() {
      this.todoItems = [];
      localStorage.clear();
    }
  },
  created() {
    if (localStorage.length > 0){
      for(var i = 0; i < localStorage.length; i++) {
        if (localStorage.key(i) !== 'loglevel:webpack-dev-server') {
          this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
          console.log(JSON.parse(localStorage.getItem(localStorage.key(i))));
        }
      }
    }
  }
}
</script>

<style>
  body {
    text-align: center;
    background-color: #F6F6F6;
  }
  input {
    border-style: groove;
    width: 200px;
  }
  button {
    border-style: groove;
  }
  .shadow {
    box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
  }
</style>
