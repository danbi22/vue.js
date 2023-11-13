<template>
  <app-header
    @changee="change"
    :appTitle="message">
  </app-header>
  <div>
    {{ message }}
  </div>
  <button @click="showAlert">경고</button>
</template>

<script>
import AppHeader from './components/AppHeader.vue'

  export default {
    components: {
      AppHeader
    },
    data() {
      return {
        message: '앱 헤더 컴포넌트'
      }
    },
    methods: {
      showAlert() {
        alert('hello');
      },
      change() {
        console.log('change()');
      }
    },
  }
</script>

<style lang="sass" scoped>

</style>