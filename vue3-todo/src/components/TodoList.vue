<template>
  <ul>
    <li v-for="item in todoList" :key="item">
      {{ item }}
      <span class="btn" @click="removeItem">-</span>
    </li>
  </ul>
</template>

<script>
  export default {
    props: ['todoList'],
    methods: {
      removeItem() {
        this.$emit('removeItem');
      }
    }
  }
</script>

<style scoped>

</style>