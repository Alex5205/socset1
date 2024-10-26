<template>
    <div class="user-card">
      <h3>{{ user.name }}</h3>
      <p>Навыки: {{ user.skills }}</p>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      user: {
        type: Object,
        required: true,
      },
    },
  };
  </script>
  
  <style scoped>
  .user-card {
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 10px;
    margin: 10px;
  }
  </style>