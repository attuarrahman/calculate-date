<template>
    <h4>Welcome from {{ showmessage() }}</h4>
  </template>
  
  <script>
  export default {
    methods: {
      showmessage() {
        return "seroza";
      }
    }
  }
  </script>
  
  <style>
  h4 {
    color: green;
    font-size: 20px;
  }
  </style>
  