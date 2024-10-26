<template>
  <div id="app">
    <h1>Социальная Сеть для Поиска Партнёра по Бизнесу</h1>
    <div v-if="!isAuthenticated">
      <LoginForm @login="handleLogin" />
      <RegisterForm @register="handleRegister" />
    </div>
    <div v-else>
      <SearchForm @search="filterUsers" />
      <UserList :users="filteredUsers" />
      <button @click="logout">Выйти</button>
    </div>
  </div>
</template>

<script>
import SearchForm from './components/SearchForm.vue';
import UserList from './components/UserList.vue';
import LoginForm from './components/LoginForm.vue';
import RegisterForm from './components/RegisterForm.vue';

export default {
  components: {
    SearchForm,
    UserList,
    LoginForm,
    RegisterForm,
  },
  data() {
    return {
      users: [
        { id: 1, name: 'Иван Иванов', password: '123456', skills: 'Маркетинг, Продажи' },
        { id: 2, name: 'Петр Петров', password: 'abcdef', skills: 'Разработка, Дизайн' },
        { id: 3, name: 'Светлана Сидорова', password: 'qwerty', skills: 'Финансы, Аналитика' },
        // Добавьте больше пользователей по необходимости
      ],
      filteredUsers: [],
      isAuthenticated: false,
      currentUser: null,
    };
  },
  mounted() {
    this.filteredUsers = this.users; // Изначально показываем всех пользователей
  },
  methods: {
    filterUsers(searchTerm) {
      this.filteredUsers = this.users.filter(user => 
        user.name.toLowerCase().includes(searchTerm.toLowerCase())
      );
    },
    handleLogin(user) {
      this.isAuthenticated = true;
      this.currentUser = user;
    },
    handleRegister(newUser) {
      this.users.push(newUser);
      this.isAuthenticated = true;
      this.currentUser = newUser;
    },
    logout() {
      this.isAuthenticated = false;
      this.currentUser = null;
    },
  },
};
</script>

<style>
#app {
  text-align: center;
}
</style>