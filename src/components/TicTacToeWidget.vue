<template>
    <div class="tic-tac-toe-widget">
      <h2>Tic Tac Toe</h2>
      <div class="board">
        <div
          v-for="(cell, index) in board"
          :key="index"
          @click="handleClick(index)"
          :class="{ 'x-cell': cell === 'X', 'o-cell': cell === 'O' }"
        >
          <div class="cell-content">
            <span v-if="cell === 'X'" class="cross">X</span>
            <span v-if="cell === 'O'" class="circle">O</span>
          </div>
        </div>
      </div>
      <button @click="resetGame">Reset</button>
      <p>{{ status }}</p>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        board: ['', '', '', '', '', '', '', '', ''],
        currentPlayer: 'X',
        isGameEnded: false,
      };
    },
    computed: {
      status() {
        if (this.isGameEnded) {
          return 'Game Over!';
        }
        return `Player ${this.currentPlayer}'s turn`;
      },
    },
    methods: {
      handleClick(index) {
        if (!this.isGameEnded && this.board[index] === '') {
          this.board[index] = this.currentPlayer;
          this.checkWinner();
          this.currentPlayer = this.currentPlayer === 'X' ? 'O' : 'X';
        }
      },
      checkWinner() {
        const winningCombinations = [
          [0, 1, 2], [3, 4, 5], [6, 7, 8], // Rows
          [0, 3, 6], [1, 4, 7], [2, 5, 8], // Columns
          [0, 4, 8], [2, 4, 6], // Diagonals
        ];
        for (const combination of winningCombinations) {
          const [a, b, c] = combination;
          if (this.board[a] && this.board[a] === this.board[b] && this.board[a] === this.board[c]) {
            this.isGameEnded = true;
            return;
          }
        }
      },
      resetGame() {
        this.board = ['', '', '', '', '', '', '', '', ''];
        this.currentPlayer = 'X';
        this.isGameEnded = false;
      },
    },
  };
  </script>
  
  <style scoped>
  .tic-tac-toe-widget {
    border: 1px solid #00bcd4;
    padding: 20px;
    margin-bottom: 20px;
    font-family: 'Segoe UI', sans-serif;
    font-size: 1.2rem;
    max-width: 300px;
    margin: 0 auto;
    text-align: center;
  }
  
  .board {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 10px;
    margin-bottom: 10px;
  }
  
  .board div {
    border: 2px solid #00bcd4;
    height: 100px;
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  .board div:hover {
    background-color: rgba(0, 0, 0, 0.1);
  }
  
  .cell-content {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  
  .cross,
  .circle {
    font-size: 2.5rem;
    font-weight: bold;
  }
  
  .cross {
    color: #ff5722;
  }
  
  .circle {
    color: #00bcd4;
  }
  
  button {
    margin-top: 20px;
    background-color: #00bcd4;
    color: #fff;
    border: none;
    padding: 10px 20px;
    font-size: 1rem;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  button:hover {
    background-color: #0097a7;
  }
  </style>
  