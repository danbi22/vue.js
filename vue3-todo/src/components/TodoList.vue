<template>
  <ul>
    <li v-for="(item, index) in todoList" :key="item" class="shadow">
      <i class="checkBtn fas fa-check" :class="{checkBtnCompleted: item.completed}" @click="toggleComplete(item)"></i>
      <span :class="{textCompleted: item.completed}">
        {{ item.name }}
      </span>
      <span class="removeBtn"  @click="removeItem(item, index)">
        <i class="removeBtn fas fa-trash-alt"></i>
      </span>
    </li>
  </ul>
</template>

<script>
  export default {
    props: ['todoList'],
    methods: {
      removeItem(item, index) {
        this.$emit('removeItem', item, index);
      },
      toggleComplete(item, index) {
        console.log(item.completed);
        item.completed = !item.completed;
        this.$emit('changeCompleted', item, index);
        console.log(item.completed);
      }
    },
  }
</script>

<style scoped>
  ul {
    list-style-type: none;
    padding-left: 0px;
    margin-top: 0;
    text-align: left;
  }
  li {
    display: flex;
    min-height: 50px;
    height: 50px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 5px;
  }
  .checkBtn {
    line-height: 45px;
    /* color: black; */
    color: #62acde;
    margin-right: 5px;
  }
  .checkBtnCompleted {
    /* color: #62acde; */
    color: black;
  }
  .textCompleted {
    text-decoration: line-through;
  }
  .removeBtn {
    margin-left: auto;
    color: #de4343;
  }
</style>