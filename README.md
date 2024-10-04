<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Message Box Form</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            background-color: #f4f4f4;
            margin: 0;
        }
        .message-box {
            background-color: white;
            border: 1px solid #ccc;
            border-radius: 10px;
            padding: 20px;
            width: 300px;
            text-align: center;
        }
        .message-box h2 {
            margin-bottom: 15px;
            font-size: 20px;
            color: #333;
        }
        .message-box label {
            font-size: 14px;
            color: #555;
            display: block;
            margin-bottom: 5px;
        }
        .message-box textarea {
            width: 100%;
            padding: 8px;
            margin-bottom: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            font-size: 14px;
            resize: none;
        }
        .message-box button {
            background-color: #007bff;
            color: white;
            border: none;
            border-radius: 5px;
            padding: 10px;
            width: 100%;
            font-size: 16px;
            cursor: pointer;
        }
        .message-box button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <div class="message-box">
        <h2>Message Form</h2>
        <label for="message">Fetched Message:</label>
        <textarea id="message" placeholder="Loading message..." readonly></textarea>
        <button type="submit" onclick="fetchMessage()">Fetch Message</button>
    </div>

    <script>
        // Function to fetch message from an external link
        function fetchMessage() {
            fetch('https://drain1103.github.io/Welcome-My-Page./')
                .then(response => response.text()) // Assuming plain text response
                .then(data => {
                    const messageTextarea = document.getElementById('message');
                    messageTextarea.value = data; // Set the fetched message in the textarea
                })
                .catch(error => {
                    console.error('Error fetching message:', error);
                });
        }

        // Automatically fetch the message when the page loads
        window.onload = fetchMessage;
    </script>
</body>
</html>
