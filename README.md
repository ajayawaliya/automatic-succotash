# automatic-succotash
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>GameHub - Play Solo and Multiplayer Games</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 0; padding: 0; background: #f4f4f4; }
        header { background: #333; color: white; padding: 1rem; text-align: center; }
        nav { display: flex; justify-content: center; gap: 1rem; margin: 1rem 0; }
        nav a { text-decoration: none; color: #333; padding: 0.5rem; background: #ddd; border-radius: 5px; }
        .game-section { max-width: 800px; margin: 2rem auto; padding: 1rem; background: white; border-radius: 8px; box-shadow: 0 0 10px rgba(0,0,0,0.1); }
        button { padding: 0.5rem 1rem; margin: 0.5rem; cursor: pointer; }
        #output { margin-top: 1rem; font-weight: bold; }
    </style>
</head>
<body>
    <header>
        <h1>GameHub</h1>
        <p>Enjoy solo and multiplayer games!</p>
    </header>
    <nav>
        <a href="#solo">Solo Games</a>
        <a href="#multi">Multiplayer Games</a>
    </nav>
    
    <section id="solo" class="game-section">
        <h2>Solo Game: Number Guessing</h2>
        <p>Guess a number between 1 and 100. The computer will tell you if it's higher or lower.</p>
        <input type="number" id="guess" placeholder="Enter your guess">
        <button onclick="checkGuess()">Guess</button>
        <div id="output"></div>
    </section>
    
    <section id="multi" class="game-section">
        <h2>Multiplayer Game: Rock-Paper-Scissors</h2>
        <p>(Placeholder: In a full implementation, connect two players via WebSockets. For now, play against a random choice.)</p>
        <button onclick="playRPS('rock')">Rock</button>
        <button onclick="playRPS('paper')">Paper</button>
        <button onclick="playRPS('scissors')">Scissors</button>
        <div id="rps-output"></div>
    </section>

    <script>
        // Solo Game: Number Guessing
        let secretNumber = Math.floor(Math.random() * 100) + 1;
        function checkGuess() {
            const guess = parseInt(document.getElementById('guess').value);
            const output = document.getElementById('output');
            if (guess === secretNumber) {
                output.textContent = 'Correct! You win!';
                secretNumber = Math.floor(Math.random() * 100) + 1; // Reset
            } else if (guess < secretNumber) {
                output.textContent = 'Too low! Try again.';
            } else {
                output.textContent = 'Too high! Try again.';
            }
        }

        // Multiplayer Placeholder: Rock-Paper-Scissors (vs. random)
        function playRPS(choice) {
            const choices = ['rock', 'paper', 'scissors'];
            const computer = choices[Math.floor(Math.random() * 3)];
            const output = document.getElementById('rps-output');
            if (choice === computer) {
                output.textContent = `You chose ${choice}, computer chose ${computer}. It's a tie!`;
            } else if ((choice === 'rock' && computer === 'scissors') || (choice === 'paper' && computer === 'rock') || (choice === 'scissors' && computer === 'paper')) {
                output.textContent = `You chose ${choice}, computer chose ${computer}. You win!`;
            } else {
                output.textContent = `You chose ${choice}, computer chose ${computer}. You lose!`;
            }
        }
    </script>
</body>
</html>
