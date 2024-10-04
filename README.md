<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Message Box</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background: linear-gradient(to right, #74ebd5, #ACB6E5); /* Gradient background */
            margin: 0;
        }
        .message-box {
            background-color: white;
            border-radius: 15px; /* More rounded corners */
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.2); /* Deeper shadow for a modern look */
            padding: 30px; /* Increased padding */
            width: 350px; /* Slightly wider box */
            text-align: center;
            transition: transform 0.3s; /* Smooth hover effect */
        }
        .message-box:hover {
            transform: scale(1.02); /* Subtle scaling on hover */
        }
        .message-box h2 {
            margin-bottom: 20px; /* Increased margin */
            color: #333;
            font-size: 24px; /* Larger font size */
        }
        .message-box label {
            margin-bottom: 8px; /* Increased margin */
            display: block;
            color: #666;
            font-weight: bold; /* Bold label text */
        }
        .message-box input, .message-box textarea {
            width: 100%;
            border-radius: 8px; /* Rounded corners */
            border: 2px solid #ddd; /* Thicker border */
            padding: 12px; /* Increased padding */
            margin-bottom: 15px; /* Increased margin */
            font-size: 16px; /* Font size */
            transition: border-color 0.3s; /* Smooth border color transition */
        }
        .message-box input:focus, .message-box textarea:focus {
            border-color: #007bff; /* Border color on focus */
            outline: none; /* Remove default outline */
        }
        .message-box textarea {
            height: 120px; /* Taller textarea */
            resize: none;
        }
        .message-box button {
            background-color: #28a745; /* Primary button color */
            color: white;
            border: none;
            border-radius: 8px; /* Rounded button corners */
            padding: 12px;
            width: 100%;
            cursor: pointer;
            font-size: 18px; /* Larger font size */
            margin-bottom: 12px; /* Increased spacing between buttons */
            transition: background-color 0.3s, transform 0.2s; /* Smooth transitions */
        }
        .message-box button:hover {
            background-color: #218838; /* Darker green on hover */
            transform: translateY(-2px); /* Lift effect */
        }
        .message-display {
            margin-top: 20px; /* Increased top margin */
            text-align: center;
            display: none; /* Hide initially */
            width: 100%;
            max-width: 400px; /* Limit maximum width */
        }
        .message {
            margin: 10px 0; /* Margin for spacing between messages */
            border-radius: 8px; /* Rounded corners */
            padding: 12px; /* Padding for better spacing */
            background: linear-gradient(135deg, #6dd5ed, #2193b0); /* Gradient background for messages */
            color: white; /* White text for better contrast */
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.3); /* Deeper shadow for messages */
            font-size: 16px; /* Font size for the message text */
            opacity: 0; /* Initially hidden for fade-in effect */
            transform: translateY(20px); /* Start slightly lower for animation */
            transition: opacity 0.5s ease, transform 0.5s ease; /* Smooth transitions */
        }
        .message.visible {
            opacity: 1; /* Fully visible */
            transform: translateY(0); /* Reset position */
        }
        .message:hover {
            box-shadow: 0 0 20px rgba(255, 255, 255, 0.7); /* Glowing effect on hover */
            transform: scale(1.02); /* Slightly scale up on hover */
        }
        .sender {
            font-weight: bold; /* Make sender's name bold */
            font-size: 18px; /* Slightly larger font size for the sender's name */
            margin-bottom: 5px; /* Space between name and message */
        }
    </style>
</head>
<body>
    <div class="message-box" id="messageBox">
        <h2>Send a Message</h2>
        <label for="sender">Your Name:</label>
        <input type="text" id="sender" placeholder="Enter your name" required>
        <label for="message">Your Message:</label>
        <textarea id="message" placeholder="Type your message here..." required></textarea>
        <button type="submit" onclick="sendMessage()">Send</button>
        <button class="open-button" onclick="openMessage()">[ Open It! 📬 ]</button>
    </div>

    <div class="message-display" id="messageDisplay"></div> <!-- Move this below the message box -->

    <script>
        let messages = []; // Store messages
        function sendMessage() {
            const senderInput = document.getElementById('sender');
            const messageInput = document.getElementById('message');
            const senderName = senderInput.value; // Get the value from the name input
            const messageText = messageInput.value; // Get the value from the textarea
            
            if (senderName && messageText) { // Check if the name and message are not empty
                messages.push({ name: senderName, text: messageText }); // Store the message with sender's name
                senderInput.value = ''; // Clear the name input
                messageInput.value = ''; // Clear the textarea
            }
        }

        function openMessage() {
            const messageDisplay = document.getElementById('messageDisplay');
            messageDisplay.innerHTML = ''; // Clear previous messages

            messages.forEach((message, index) => {
                const messageDiv = document.createElement('div');
                messageDiv.className = 'message'; // Class for styling messages
                messageDiv.innerHTML = `<div class="sender">${message.name}</div><div>${message.text}</div>`; // Set the message text and sender name
                messageDisplay.appendChild(messageDiv); // Append each message
                
                // Trigger the visible class after a short delay for animation
                setTimeout(() => {
                    messageDiv.classList.add('visible');
                }, index * 100); // Stagger the appearance
            });

            messageDisplay.style.display = 'block'; // Show the message display
            document.getElementById('messageBox').classList.add('hidden'); // Hide the input box
        }
    </script>
</body>
</html>
