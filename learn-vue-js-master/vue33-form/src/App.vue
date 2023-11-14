<template>
  <form action="" @submit.prevent="submitForm">
    <div>
      <label for="userId">ID: </label>
      <input id="userId" type="text" v-model="userId">
    </div>
    <div>
      <label for="password">PW: </label>
      <input id="password" type="text" v-model="password">
    </div>
    <button type="submit">로그인</button>
  </form>
</template>

<script>
  import axois from 'axios'
  import { ref } from 'vue';

  export default {
    setup() {
      // data()
      const userId = ref('');
      const password = ref('');

      // methods:
      const submitForm = () => {
        axois.post('https://jsonplaceholder.typicode.com/users/', {
          userId: userId.value,
          password: password.value
        })
        .then(response => console.log(response.data))
        .catch(error => console.log(error));
      }
    }
    // data() {
    //   return {
    //     userId: '',
    //     password: '',
    //   }
    // },
    // methods: {
    //   submitForm() {
    //     axois.post('https://jsonplaceholder.typicode.com/users/', {
    //       userId: this.userId,
    //       password: this.password,
    //     })
    //     .then(response => console.log(response))
    //     .catch(error => console.log(error));
    //     console.log('제출됨');
    //   }
    // }
  }
</script>

<style scoped>

</style>