<template>
    <div class="scoreboard">
      <h2>Scoreboard</h2>
      <p>Player: {{ playerScore }}</p>
      <p>Computer: {{ computerScore }}</p>
    </div>
  </template>
  
  <script>
  export default {
    props: ['playerScore', 'computerScore']
  }
  </script>
  
  <style scoped>
  .scoreboard {
    text-align: center;
    margin-bottom: 20px;
  }
  </style>
  