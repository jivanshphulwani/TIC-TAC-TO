<!DOCTYPE html>
<html>
<head>
	<title>Tic Tac Toe</title>
	<style>
		#game-board {
			display: grid;
			grid-template-columns: repeat(3, 1fr);
			grid-gap: 10px;
		}
		.cell {
			background-color: #f0f0f0;
			padding: 20px;
			border: black;
			border-radius: 10px;
			cursor: pointer;
		}
	</style>
</head>
<body>
	<h1>Tic Tac Toe</h1>
	<div id="game-board">
		<button class="cell" onclick="makeMove(this, 0)"></button>
		<button class="cell" onclick="makeMove(this, 1)"></button>
		<button class="cell" onclick="makeMove(this, 2)"></button>
		<button class="cell" onclick="makeMove(this, 3)"></button>
		<button class="cell" onclick="makeMove(this, 4)"></button>
		<button class="cell" onclick="makeMove(this, 5)"></button>
		<button class="cell" onclick="makeMove(this, 6)"></button>
		<button class="cell" onclick="makeMove(this, 7)"></button>
		<button class="cell" onclick="makeMove(this, 8)"></button>
	</div>

	<script>
		let currentPlayer = 'X';
		let gameBoard = ['', '', '', '', '', '', '', '', ''];

		function makeMove(cell, index) {
			if (gameBoard[index] === '') {
				gameBoard[index] = currentPlayer;
				cell.textContent = currentPlayer;

				if (checkWinner()) {
					alert(`Player ${currentPlayer} wins!`);
					resetGame();
				} else {
					currentPlayer = currentPlayer === 'X' ? 'O' : 'X';
				}
			}
		}

		function checkWinner() {
			const winningCombinations = [
				[0, 1, 2],
				[3, 4, 5],
				[6, 7, 8],
				[0, 3, 6],
				[1, 4, 7],
				[2, 5, 8],
				[0, 4, 8],
				[2, 4, 6]
			];

			for (const combination of winningCombinations) {
				if (gameBoard[combination[0]] === gameBoard[combination[1]] &&
					gameBoard[combination[1]] === gameBoard[combination[2]] &&
					gameBoard[combination[0]] !== '') {
					return true;
				}
			}

			return false;
		}

		function resetGame() {
			gameBoard = ['', '', '', '', '', '', '', '', ''];
			currentPlayer = 'X';
			const cells = document.querySelectorAll('.cell');
			cells.forEach(cell => cell.textContent = '');
		}
	</script>
</body>
</html>
