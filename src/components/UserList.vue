<template>
    <div>
      <h2>Список пользователей</h2>
      <div v-if="users.length === 0">Нет пользователей для отображения!</div>
      <div v-else>
        <UserCard 
          v-for="user in users" 
          :key="user.id" 
          :user="user" 
        />
      </div>
    </div>
  </template>
  
  <script>
  import UserCard from './UserCard.vue';
  
  export default {
    components: {
      UserCard,
    },
    props: {
      users: {
        type: Array,
        required: true,
      },
    },
  };
  </script>
  
  <style scoped>
  h2 {
    margin-top: 20px;
  }
  </style>