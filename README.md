![image](https://github.com/i-ouellette/i-ouellette/assets/157050094/8a4eab11-47fd-4570-a199-00a08d210791)
<h1 align="center">Hi, I'm Isaac!</h1>

<p align="center" width="150px">I am a first year Computer Science Student, Studying at <a href="https://www.queensu.ca/"><b>Queen's University.</b></a> I am really hoping to specialize in <a href= "https://www.cs.queensu.ca/undergraduate/programs/options/data-analytics.php"><b>Data Science</b></a> 🖥️ this coming year. <br> Have fun Scrolling!</p>
<p align="center"><b>Profile Visits:</b></p>
<p align="center"><img src="https://profile-counter.glitch.me/%7Bi-ouellette%7D/count.svg" alt="visitor badge"/></p>
<p align="center"><img src="https://github-readme-stats.vercel.app/api/top-langs/?username=i-ouellette&layout=compact&hide=TSQL&theme=blue_navy"></p>
<p align="center" ><img src="https://github-readme-stats.vercel.app/api?username=i-ouellette&count_private=true&show_icons=true&&theme=blue_navy&include_all_commits=true" width="400"></p> 

<p align="center">
  <img src="https://img.shields.io/badge/Connect%204-Game-blue" alt="Connect 4 Game">
</p>

<h1 align="center">Connect 4 Game</h1>

<div align="center">
  <button onclick="resetGame()">Reset Game</button>
</div>

<div align="center" id="board">
</div>

<script>
  const rows = 6;
  const columns = 7;
  let currentPlayer = 'red';
  let gameBoard = createEmptyBoard();

  function createEmptyBoard() {
    return Array.from({ length: rows }, () => Array(columns).fill(null));
  }

  function createBoardHTML() {
    const boardElement = document.getElementById('board');
    boardElement.innerHTML = '';

    for (let row = 0; row < rows; row++) {
      for (let col = 0; col < columns; col++) {
        const cell = document.createElement('div');
        cell.classList.add('cell');
        cell.dataset.row = row;
        cell.dataset.col = col;
        cell.onclick = () => dropPiece(col);

        if (gameBoard[row][col]) {
          cell.classList.add(gameBoard[row][col]);
        }

        boardElement.appendChild(cell);
      }
    }
  }

  function dropPiece(col) {
    for (let row = rows - 1; row >= 0; row--) {
      if (!gameBoard[row][col]) {
        gameBoard[row][col] = currentPlayer;
        currentPlayer = currentPlayer === 'red' ? 'yellow' : 'red';
        createBoardHTML();
        checkWinner(row, col);
        return;
      }
    }
  }

  function checkWinner(row, col) {
    // Add your logic to check for a winner
    // This can include checking horizontally, vertically, and diagonally
  }

  function resetGame() {
    gameBoard = createEmptyBoard();
    currentPlayer = 'red';
    createBoardHTML();
  }

  createBoardHTML();
</script>

<style>
  #board {
    display: grid;
    grid-template-columns: repeat(7, 50px);
    gap: 5px;
  }

  .cell {
    width: 50px;
    height: 50px;
    border: 1px solid #000;
    cursor: pointer;
  }

  .red {
    background-color: red;
    border-radius: 50%;
  }

  .yellow {
    background-color: yellow;
    border-radius: 50%;
  }
</style>
