---
layout: base
title: Tic Tac Toe Game
description: Tic Tac Toe Game
hide: true
---

# ticTacToe game

[ticTacToe](https://yrzeni.github.io/nephis./ticTacToe.md)




Play the Tic-Tac-Toe game below.
</run>
<div style="display: flex; justify-content: center; align-items: center; flex-direction: column; height: 100vh; background-color: #f4f4f4; margin: 0;">

  <div class="game-container" style="display: grid; grid-template-columns: repeat(3, 100px); grid-template-rows: repeat(3, 100px); gap: 5px;">
    <div class="cell" data-cell="0" style="width: 100px; height: 100px; display: flex; justify-content: center; align-items: center; background-color: #fff; border: 1px solid #ccc; font-size: 2em; cursor: pointer;"></div>
    <div class="cell" data-cell="1" style="width: 100px; height: 100px; display: flex; justify-content: center; align-items: center; background-color: #fff; border: 1px solid #ccc; font-size: 2em; cursor: pointer;"></div>
    <div class="cell" data-cell="2" style="width: 100px; height: 100px; display: flex; justify-content: center; align-items: center; background-color: #fff; border: 1px solid #ccc; font-size: 2em; cursor: pointer;"></div>
    <div class="cell" data-cell="3" style="width: 100px; height: 100px; display: flex; justify-content: center; align-items: center; background-color: #fff; border: 1px solid #ccc; font-size: 2em; cursor: pointer;"></div>
    <div class="cell" data-cell="4" style="width: 100px; height: 100px; display: flex; justify-content: center; align-items: center; background-color: #fff; border: 1px solid #ccc; font-size: 2em; cursor: pointer;"></div>
    <div class="cell" data-cell="5" style="width: 100px; height: 100px; display: flex; justify-content: center; align-items: center; background-color: #fff; border: 1px solid #ccc; font-size: 2em; cursor: pointer;"></div>
    <div class="cell" data-cell="6" style="width: 100px; height: 100px; display: flex; justify-content: center; align-items: center; background-color: #fff; border: 1px solid #ccc; font-size: 2em; cursor: pointer;"></div>
    <div class="cell" data-cell="7" style="width: 100px; height: 100px; display: flex; justify-content: center; align-items: center; background-color: #fff; border: 1px solid #ccc; font-size: 2em; cursor: pointer;"></div>
    <div class="cell" data-cell="8" style="width: 100px; height: 100px; display: flex; justify-content: center; align-items: center; background-color: #fff; border: 1px solid #ccc; font-size: 2em; cursor: pointer;"></div>
  </div>

  <div class="status" style="margin-bottom: 20px; font-size: 1.5em;">Player X's turn</div>
  <button class="reset-btn" onclick="resetGame()" style="padding: 10px 20px; font-size: 1em; cursor: pointer; background-color: #4CAF50; color: white; border: none; border-radius: 5px; margin-top: 20px;">Reset Game</button>
</div>

<script>
  const cells = document.querySelectorAll('.cell');
  let currentPlayer = 'X';
  let board = ['', '', '', '', '', '', '', '', ''];
  let gameActive = true;

  const winningConditions = [
    [0, 1, 2],
    [3, 4, 5],
    [6, 7, 8],
    [0, 3, 6],
    [1, 4, 7],
    [2, 5, 8],
    [0, 4, 8],
    [2, 4, 6]
  ];

  function handleCellClick(e) {
    const index = e.target.getAttribute('data-cell');

    if (board[index] !== '' || !gameActive) return;

    board[index] = currentPlayer;
    e.target.textContent = currentPlayer;
    e.target.classList.add('clicked');

    if (checkWinner()) {
      document.querySelector('.status').textContent = `${currentPlayer} wins!`;
      gameActive = false;
      return;
    }

    currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
    document.querySelector('.status').textContent = `Player ${currentPlayer}'s turn`;
  }

  function checkWinner() {
    return winningConditions.some(combination => {
      const [a, b, c] = combination;
      return board[a] === currentPlayer && board[b] === currentPlayer && board[c] === currentPlayer;
    });
  }

  function resetGame() {
    board = ['', '', '', '', '', '', '', '', ''];
    gameActive = true;
    currentPlayer = 'X';
    cells.forEach(cell => {
      cell.textContent = '';
      cell.classList.remove('clicked');
    });
    document.querySelector('.status').textContent = `Player X's turn`;
  }

  cells.forEach(cell => {
    cell.addEventListener('click', handleCellClick);
  });
</run>


