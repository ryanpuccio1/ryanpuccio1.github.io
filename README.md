<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chatxo - Go Live</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #1a1a1a;
            color: white;
        }
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 15px;
            background-color: #333;
        }
        header h1 {
            color: #ff69b4;
            margin: 0;
            font-size: 1.8em;
        }
        header .nav-buttons button {
            background: #ff69b4;
            color: white;
            border: none;
            border-radius: 5px;
            padding: 10px 15px;
            margin-left: 10px;
            cursor: pointer;
            font-size: 1em;
        }
        header .nav-buttons button:hover {
            background: #e04898;
        }
        .container {
            padding: 20px;
            text-align: center;
        }
        .chat-container {
            margin: 20px auto;
            max-width: 800px;
            background: #2c2c2c;
            border-radius: 8px;
            padding: 20px;
        }
        .viewer-count {
            font-size: 1.2em;
            margin-bottom: 10px;
        }
        .messages {
            height: 300px;
            overflow-y: auto;
            border: 1px solid #444;
            padding: 10px;
            border-radius: 4px;
            background: #1e1e1e;
        }
        .message {
            margin-bottom: 10px;
        }
        .message span {
            font-weight: bold;
            color: #ff69b4;
        }
        .donation {
            color: #ffd700;
        }
        .fake-input {
            display: flex;
            margin-top: 15px;
        }
        .fake-input input {
            flex: 1;
            padding: 10px;
            border: 1px solid #444;
            border-radius: 4px;
            background: #1e1e1e;
            color: white;
        }
        .fake-input button {
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            background: #ff69b4;
            color: white;
            margin-left: 10px;
            cursor: pointer;
        }
        .fake-input button:hover {
            background: #e04898;
        }
    </style>
</head>
<body>
    <header>
        <h1>Chatxo</h1>
        <div class="nav-buttons">
            <button onclick="goLive()">Go Live</button>
            <button onclick="openSettings()">Settings</button>
            <button onclick="openAccount()">Account</button>
        </div>
    </header>
    <div class="container" id="home">
        <h2>Welcome to Chatxo</h2>
        <p>Your platform for connecting live. Explore, chat, and enjoy the experience.</p>
    </div>
    <div class="container chat-container" id="chat">
        <div class="viewer-count">Viewers: <span id="viewerCount">75</span></div>
        <div class="messages" id="messages"></div>
        <div class="fake-input">
            <input type="text" id="userMessage" placeholder="Type your message...">
            <button onclick="sendMessage()">Send</button>
        </div>
    </div>

    <script>
        const messages = document.getElementById('messages');
        const viewerCount = document.getElementById('viewerCount');

        // Simulate slow viewer fluctuation
        setInterval(() => {
            const change = Math.random() < 0.5 ? 1 : -1;
            const currentViewers = parseInt(viewerCount.textContent);
            if (currentViewers + change >= 68 && currentViewers + change <= 80) {
                viewerCount.textContent = currentViewers + change;
            }
        }, 5000);

        // Simulate random comments
        setInterval(() => {
            if (Math.random() < 0.5) return; // 50% chance of no new message

            const fakeComments = [
                { user: 'viewer88', message: 'Love the vibe here!' },
                { user: 'donor23', message: 'Donated $10 - Keep it up!', isDonation: true },
                { user: 'fan123', message: 'Amazing content, keep going!' },
                { user: 'newFan22', message: 'Just joined, this is awesome!' }
            ];

            const randomComment = fakeComments[Math.floor(Math.random() * fakeComments.length)];
            const newMessage = document.createElement('div');
            newMessage.classList.add('message');
            if (randomComment.isDonation) newMessage.classList.add('donation');

            newMessage.innerHTML = `<span>${randomComment.user}:</span> ${randomComment.message}`;
            messages.appendChild(newMessage);
            messages.scrollTop = messages.scrollHeight;
        }, 8000);

        // User sends a message
        function sendMessage() {
            const userMessage = document.getElementById('userMessage').value;
            if (!userMessage) return;

            const newMessage = document.createElement('div');
            newMessage.classList.add('message');
            newMessage.innerHTML = `<span>You:</span> ${userMessage}`;
            messages.appendChild(newMessage);
            messages.scrollTop = messages.scrollHeight;

            document.getElementById('userMessage').value = '';
        }

        function goLive() {
            alert('Go Live functionality coming soon!');
        }

        function openSettings() {
            alert('Settings page coming soon!');
        }

        function openAccount() {
            alert('Account creation coming soon!');
        }
    </script>
</body>
</html>
