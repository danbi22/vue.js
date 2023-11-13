<template>
  <h1>{{ appTitle }}</h1>
  <button @click="change">change</button>
</template>

<script>
  export default {
    props: ['appTitle'],
    methods: {
      change() {
        this.$emit('changee')
      }
    }
  }
</script>

<style scoped>

</style>