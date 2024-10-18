<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>9 Slot Reward Game</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #4b79a1; /* Gradient background color */
            background: linear-gradient(135deg, #4b79a1 0%, #283e51 100%);
            color: #fff;
            text-align: center;
        }
        .slot-machine {
            width: 400px;
            margin: 20px auto;
            border: 5px solid #fff;
            border-radius: 10px;
            background-color: rgba(255, 255, 255, 0.2); /* Semi-transparent white background */
            padding: 20px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.8);
        }
        .reels {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 10px;
            margin-bottom: 20px;
        }
        .reel {
            width: 100px;
            height: 100px;
            background-color: rgba(255, 255, 255, 0.1); /* Lighter transparent background */
            border: 2px solid #fff;
            border-radius: 5px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 36px; /* Bigger symbols */
            transition: transform 0.5s;
        }
        .spin-button, .reset-button {
            padding: 12px 25px;
            font-size: 20px;
            margin: 5px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            transition: background-color 0.3s, transform 0.2s;
        }
        .spin-button {
            background-color: #28a745;
            color: #fff;
        }
        .spin-button:hover {
            background-color: #218838;
            transform: scale(1.05); /* Scale effect on hover */
        }
        .reset-button {
            background-color: #dc3545;
            color: #fff;
        }
        .reset-button:hover {
            background-color: #c82333;
            transform: scale(1.05); /* Scale effect on hover */
        }
        .result {
            margin-top: 20px;
            font-size: 24px; /* Increased font size */
            display: none; /* Hide the result initially */
        }
        .total-wins, .account-balance {
            margin-top: 20px;
            font-size: 24px;
        }
        .payout-table {
            margin-top: 20px;
            border-collapse: collapse;
            width: 100%;
            color: #fff;
        }
        .payout-table th, .payout-table td {
            border: 1px solid #fff;
            padding: 8px;
            text-align: center;
        }
        .payout-table th {
            background-color: rgba(255, 255, 255, 0.3); /* Light background for headers */
        }
        .winning-history {
            margin-top: 20px;
            text-align: left;
            color: #fff;
        }
        .loss {
            background-color: rgba(255, 0, 0, 0.7); /* Red background for loss */
            color: black;
        }
    </style>
</head>
<body>
    <h1>9 Slot Reward Game</h1>
    <div class="bet-container">
        <label for="betAmount">Bet Amount: </label>
        <input type="number" id="betAmount" value="10" min="1" style="padding: 8px; font-size: 18px;">
    </div>

    <div class="account-balance" id="accountBalance">Account Balance: 100</div> <!-- Account balance display -->

    <div class="slot-machine">
        <h2>Slot Machine</h2>
        <div class="reels" id="reels">
            <div class="reel" id="reel1">🍒</div>
            <div class="reel" id="reel2">🍒</div>
            <div class="reel" id="reel3">🍒</div>
            <div class="reel" id="reel4">🍒</div>
            <div class="reel" id="reel5">🍒</div>
            <div class="reel" id="reel6">🍒</div>
            <div class="reel" id="reel7">🍒</div>
            <div class="reel" id="reel8">🍒</div>
            <div class="reel" id="reel9">🍒</div>
        </div>
        <div class="result" id="result"></div>
    </div>

    <button class="spin-button" onclick="spin()">Spin!</button>
    <button class="reset-button" onclick="reset()">Reset</button>
    
    <div class="total-wins" id="totalWins">Total Wins: 0</div>

    <h2>Payout Table</h2>
    <table class="payout-table" id="payoutTable">
        <tr>
            <th>Combination</th>
            <th>Payout</th>
        </tr>
        <tr>
            <td>3 🍒</td>
            <td>5x</td> <!-- Reduced payout -->
        </tr>
        <tr>
            <td>2 🍒</td>
            <td>1x</td> <!-- Reduced payout -->
        </tr>
        <tr>
            <td>3 🍋</td>
            <td>6x</td>
        </tr>
        <tr>
            <td>3 🍊</td>
            <td>4x</td> <!-- Reduced payout -->
        </tr>
        <tr>
            <td>3 🍉</td>
            <td>3x</td> <!-- Reduced payout -->
        </tr>
        <tr>
            <td>3 ⭐</td>
            <td>15x</td>
        </tr>
        <tr>
            <td>3 🍀</td>
            <td>10x</td>
        </tr>
        <tr>
            <td>3 💰</td>
            <td>30x</td>
        </tr>
    </table>

    <div class="winning-history" id="winningHistory"></div>

    <audio id="spinSound" src="spin-sound.mp3"></audio>
    <audio id="winSound" src="win-sound.mp3"></audio>

    <script>
        let totalWins = 0;
        let winningHistory = [];
        let accountBalance = 100; // Initial account balance
        let spinCount = 0; // Track the number of spins

        function spin() {
            const betAmount = parseInt(document.getElementById('betAmount').value);

            // Check if the bet amount is valid
            if (betAmount > accountBalance) {
                alert("Insufficient balance! Please reduce your bet amount.");
                return;
            }

            // Check for special case of total bet amount
            if (totalWins >= 1000) {
                accountBalance -= 1100; // Deduct 1100 for total bet amount of 1000
                document.getElementById('result').textContent = `You lost: $1100 (Total Bet: $1000)`;
            } else {
                accountBalance -= betAmount; // Deduct normal bet amount
            }

            document.getElementById('accountBalance').textContent = `Account Balance: ${accountBalance}`;

            const symbols = ['🍒', '🍋', '🍊', '🍉', '⭐', '🍀', '💰'];
            const results = [];

            for (let i = 1; i <= 9; i++) {
                const symbol = weightedRandomSymbol(); // Use weighted random selection
                document.getElementById(`reel${i}`).textContent = symbol;
                results.push(symbol);
            }

            // Spin animation
            for (let i = 1; i <= 9; i++) {
                document.getElementById(`reel${i}`).style.transform = 'rotateY(360deg)';
            }

            // Play spin sound
            document.getElementById('spinSound').play();

            setTimeout(() => {
                let winAmount = 0;
                const symbolCounts = {};

                // Count occurrences of each symbol
                results.forEach(symbol => {
                    symbolCounts[symbol] = (symbolCounts[symbol] || 0) + 1;
                });

                // Calculate winnings based on symbol counts
                for (const [symbol, count] of Object.entries(symbolCounts)) {
                    if (count >= 3) { // Winning combinations
                        winAmount += getPayout(symbol) * betAmount;
                    }
                }

                // Determine win/lose outcome based on adjusted chances
                if (Math.random() <= 0.45) { // 45% chance to win
                    accountBalance += winAmount; // Update account balance
                    totalWins += winAmount; // Update total wins
                    winningHistory.push(`Won: $${winAmount}`); // Update winning history
                    document.getElementById('winSound').play(); // Play win sound
                    document.getElementById('result').textContent = `You won: $${winAmount}`;
                } else {
                    // Losing scenario
                    document.getElementById('result').textContent = `You lost: $${betAmount}`;
                    winningHistory.push(`Lost: $${betAmount}`); // Update winning history
                }

                // Update account balance display
                document.getElementById('accountBalance').textContent = `Account Balance: ${accountBalance}`;
                
                // Update history display
                document.getElementById('winningHistory').innerHTML = winningHistory.join('<br>');
                document.getElementById('totalWins').textContent = `Total Wins: ${totalWins}`;
                document.getElementById('result').style.display = 'block'; // Show the result
            }, 2000); // Delay result display for 2 seconds
        }

        function weightedRandomSymbol() {
            const symbols = ['🍒', '🍋', '🍊', '🍉', '⭐', '🍀', '💰'];
            const weights = [10, 10, 10, 10, 2, 2, 1]; // Adjust weights here
            const totalWeight = weights.reduce((acc, weight) => acc + weight, 0);
            const randomNum = Math.random() * totalWeight;

            let weightSum = 0;
            for (let i = 0; i < symbols.length; i++) {
                weightSum += weights[i];
                if (randomNum <= weightSum) {
                    return symbols[i];
                }
            }
        }

        function reset() {
            totalWins = 0;
            accountBalance = 100; // Reset balance to initial value
            winningHistory = [];
            document.getElementById('accountBalance').textContent = `Account Balance: ${accountBalance}`;
            document.getElementById('winningHistory').innerHTML = ''; // Clear winning history
            document.getElementById('totalWins').textContent = `Total Wins: ${totalWins}`;
            document.getElementById('result').style.display = 'none'; // Hide the result
            for (let i = 1; i <= 9; i++) {
                document.getElementById(`reel${i}`).textContent = '🍒'; // Reset reels to initial state
            }
        }

        function getPayout(symbol) {
            switch (symbol) {
                case '🍒':
                    return 5; // Reduced payout
                case '🍋':
                    return 6;
                case '🍊':
                    return 4; // Reduced payout
                case '🍉':
                    return 3; // Reduced payout
                case '⭐':
                    return 15;
                case '🍀':
                    return 10;
                case '💰':
                    return 30;
                default:
                    return 0;
            }
        }
    </script>
</body>
</html>
