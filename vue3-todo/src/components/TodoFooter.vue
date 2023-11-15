<template>
  <span class="btn" @click="clearAll">Clear All</span>
</template>

<script>
  export default {
    methods: {
      clearAll() {
        this.$emit('clearAll');
      }
    }
  }
</script>

<style scoped>

</style>