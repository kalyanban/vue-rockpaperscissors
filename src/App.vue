<template>
    <div id="app">
      <ScoreBoard :playerScore="playerScore" :computerScore="computerScore" />
      <GamePlay @update-score="updateScore" />
    </div>
  </template>
  
  <script>
  import ScoreBoard from "./components/ScoreBoard"
  import GamePlay from "./components/GamePlay"
  
  export default {
    components: {
      ScoreBoard,
      GamePlay
    },
    data() {
      return {
        playerScore: 0,
        computerScore: 0
      };
    },
    methods: {
      updateScore(winner) {
        if (winner === 'player') {
          this.playerScore++;
        } else if (winner === 'computer') {
          this.computerScore++;
        }
      }
    }
  }
  </script>
  
  <style>
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  </style>
  