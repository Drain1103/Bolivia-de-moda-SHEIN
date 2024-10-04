<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Beautiful Lucky Spin Wheel</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            flex-direction: column;
            height: 100vh;
            background: linear-gradient(to bottom right, #e0f7fa, #b2ebf2);
            font-family: 'Arial', sans-serif;
            margin: 0;
        }
        h1 {
            margin-bottom: 20px;
            color: #00695c;
            text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.2);
        }
        .wheel-container {
            position: relative;
            width: 300px;
            height: 300px;
            border-radius: 50%;
            overflow: hidden;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.3);
            background-color: #fff;
        }
        .wheel {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background: conic-gradient(
                #ffcc00 0% 50%,   /* 50% - Reward 1 */
                #ff5722 50% 100%   /* 50% - Reward 2 */
            );
            transition: transform 2s ease-out;
            border: 10px solid #fff; /* White border for a clean look */
        }
        .pointer {
            position: absolute;
            top: -20px;
            left: 50%;
            transform: translateX(-50%);
            width: 0;
            height: 0;
            border-left: 15px solid transparent;
            border-right: 15px solid transparent;
            border-bottom: 20px solid #ff4081; /* Pointer color */
            z-index: 1;
        }
        button {
            margin-top: 20px;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            background-color: #00796b;
            color: white;
            font-size: 16px;
            cursor: pointer;
            transition: background-color 0.3s ease;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.3);
        }
        button:hover {
            background-color: #004d40;
            transform: translateY(-2px);
            box-shadow: 0 6px 8px rgba(0, 0, 0, 0.3);
        }
        #rewardMessage {
            margin-top: 15px;
            font-size: 18px;
            color: #00796b;
            font-weight: bold;
            text-align: center;
        }
    </style>
</head>
<body>

<h1>Lucky Spin Wheel!</h1>
<div class="wheel-container">
    <div class="pointer"></div>
    <div class="wheel" id="wheel"></div>
</div>
<button onclick="spinWheel(3)">Spin the Wheel!</button>
<div id="rewardMessage"></div>

<script>
    let isSpinning = false; // To prevent multiple spins at the same time

    function spinWheel(spinCount) {
        if (isSpinning) return; // Prevent spinning if already in progress
        isSpinning = true; // Set spinning state to true

        const wheel = document.getElementById('wheel');
        const spinDuration = 2000; // Duration for one spin in milliseconds
        let totalRotation = 0;

        // Function to perform spins
        const performSpin = (count) => {
            if (count > 0) {
                // Generate a random degree to spin (faster)
                const randomDegree = Math.floor(Math.random() * 360 + 720); // Spin at least 2 full rotations
                totalRotation += randomDegree; // Keep track of total rotation
                wheel.style.transition = `transform ${spinDuration}ms ease-out`; // Set spin duration
                wheel.style.transform = `rotate(${totalRotation}deg)`; // Apply the rotation

                // After the spin, call performSpin recursively for the next spin
                setTimeout(() => performSpin(count - 1), spinDuration);
            } else {
                // Show result only once after all spins
                document.getElementById('rewardMessage').innerText = 'You won: 50000မပေးဘူး';
                isSpinning = false; // Reset spinning state
            }
        };

        // Start the spins
        performSpin(spinCount);
    }
</script>

</body>
</html>
