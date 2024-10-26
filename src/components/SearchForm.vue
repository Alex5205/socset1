<template>
    <div>
      <input 
        type="text" 
        v-model="searchTerm" 
        @input="onSearch" 
        placeholder="Поиск партнёра по имени..."
      />
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        searchTerm: '',
      };
    },
    methods: {
      onSearch() {
        this.$emit('search', this.searchTerm);
      },
    },
  };
  </script>
  
  <style scoped>
  input {
    padding: 10px;
    width: 300px;
    margin-top: 20px;
  }
  </style>