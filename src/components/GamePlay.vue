<template>
    <div class="gameplay">
      <h2>Rock-Paper-Scissors</h2>
      <div class="choices">
        <button @click="makeChoice('rock')">Rock</button>
        <button @click="makeChoice('paper')">Paper</button>
        <button @click="makeChoice('scissors')">Scissors</button>
      </div>
      <div class="result">
        <p>Player chose: {{ playerChoice }}</p>
        <p>Computer chose: {{ computerChoice }}</p>
        <p>{{ resultMessage }}</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        playerChoice: '',
        computerChoice: '',
        resultMessage: ''
      };
    },
    methods: {
      makeChoice(choice) {
        this.playerChoice = choice;
        const choices = ['rock', 'paper', 'scissors'];
        this.computerChoice = choices[Math.floor(Math.random() * 3)];
        this.determineWinner();
      },
      determineWinner() {
        if (this.playerChoice === this.computerChoice) {
          this.resultMessage = 'It\'s a tie!';
        } else if (
          (this.playerChoice === 'rock' && this.computerChoice === 'scissors') ||
          (this.playerChoice === 'paper' && this.computerChoice === 'rock') ||
          (this.playerChoice === 'scissors' && this.computerChoice === 'paper')
        ) {
          this.resultMessage = 'Player wins!';
          this.$emit('update-score', 'player');
        } else {
          this.resultMessage = 'Computer wins!';
          this.$emit('update-score', 'computer');
        }
      }
    }
  }
  </script>
  
  <style scoped>
  .gameplay {
    text-align: center;
  }
  .choices button {
    margin: 5px;
    padding: 10px 20px;
    font-size: 16px;
  }
  .result {
    margin-top: 20px;
  }
  </style>
  