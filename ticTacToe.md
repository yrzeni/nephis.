# Tic-Tac-Toe Game

Welcome to the Tic-Tac-Toe game! Play the game below:

<div id="game-container">
  <style>
    body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      background-color: #f0f0f0;
    }

    .board {
      display: grid;
      grid-template-columns: repeat(3, 100px);
      grid-template-rows: repeat(3, 100px);
      gap: 5px;
    }

    .cell {
      width: 100px;
      height: 100px;
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 24px;
      background-color: white;
      border: 2px solid #333;
      cursor: pointer;
    }

    .cell:hover {
      background-color: #f0f0f0;
    }

    .message {
      margin-top: 20px;
      font-size: 20px;
    }

    .reset {
      margin-top: 20px;
      padding: 10px 20px;
      font-size: 16px;
      cursor: pointer;
    }

    .reset:hover {
      background-color: #f0f0f0;
    }
  </style>

  <div class="board" id="board">
    <!-- Cells will be inserted here by JavaScript -->
  </div>
  <div class="message" id="message"></div>
  <button class="reset" id="resetButton">Reset Game</button>

  <script>
    const board = document.getElementById('board');
    const message = document.getElementById('message');
    const resetButton = document.getElementById('resetButton');
    let currentPlayer = 'X';
    let gameBoard = ['', '', '', '', '', '', '', '', ''];
    let gameOver = false;

    function createBoard() {
      for (let i = 0; i < 9; i++) {
        const cell = document.createElement('div');
