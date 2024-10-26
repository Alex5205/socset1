<template>
    <div>
      <h2>Вход</h2>
      <input type="text" v-model="username" placeholder="Имя пользователя" />
      <input type="password" v-model="password" placeholder="Пароль" />
      <button @click="login">Войти</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        username: '',
        password: '',
      };
    },
    methods: {
      login() {
        const user = this.$parent.users.find(
          (user) => user.name === this.username && user.password === this.password
        );
        if (user) {
          this.$emit('login', user);
        } else {
          alert('Неверное имя пользователя или пароль');
        }
      },
    },
  };
  </script>
  
  <style scoped>
  input {
    margin: 5px;
  }
  </style>