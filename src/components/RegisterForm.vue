<template>
    <div>
      <h2>Регистрация</h2>
      <input type="text" v-model="name" placeholder="Имя пользователя" />
      <input type="password" v-model="password" placeholder="Пароль" />
      <input type="text" v-model="skills" placeholder="Навыки (через запятую)" />
      <button @click="register">Зарегистрироваться</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        name: '',
        password: '',
        skills: '',
      };
    },
    methods: {
      register() {
        const newUser = {
          id: Date.now(), // Простой способ сгенерировать уникальный ID
          name: this.name,
          password: this.password,
          skills: this.skills,
        };
        this.$emit('register', newUser);
        this.resetForm();
      },
      resetForm() {
        this.name = '';
        this.password = '';
        this.skills = '';
      },
    },
  };
  </script>
  
  <style scoped>
  input {
    margin: 5px;
  }
  </style>