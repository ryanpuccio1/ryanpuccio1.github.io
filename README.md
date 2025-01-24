<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chatxo</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #1a1a1a;
            color: white;
        }
        header {
            background-color: #333;
            padding: 20px;
            text-align: center;
        }
        header h1 {
            color: #ff69b4;
            font-size: 2.5em;
            margin: 0;
        }
        nav {
            text-align: center;
            margin-top: 20px;
        }
        nav a {
            color: #ff69b4;
            text-decoration: none;
            margin: 0 15px;
            font-size: 1.2em;
        }
        nav a:hover {
            text-decoration: underline;
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
    </header>
    <nav>
        <a href="#home">Home</a>
        <a href="#chat">Live Chat</a>
    </nav>
    <div class="container" id="home">
        <h2>Welcome to Chatxo</h2>
        <p>Your platform for connecting live. Explore, chat, and enjoy the experience.</p>
    </div>
    <div class="container chat-container" id="chat">
        <div class="viewer-count">Viewers: <span id="viewerCount">100</span></div>
        <div class="messages" id="messages">
            <div class="message"><span>viewer123:</span> You're amazing!</div>
            <div class="message donation"><span>donor45:</span> Donated $10 - Keep it up!</div>
            <div class="message"><span>viewer56:</span> So cool to see this!</div>
        </div>
        <div class="fake-input">
            <input type="text" id="userMessage" placeholder="Type your message...">
            <button onclick="sendMessage()">Send</button>
        </div>
    </div>

    <script>
        const messages = document.getElementById('messages');
        const viewerCount = document.getElementById('viewerCount');

        // Simulate fake viewer count fluctuation
        setInterval(() => {
            const viewers = Math.floor(Math.random() * (153 - 40 + 1)) + 40;
            viewerCount.textContent = viewers;
        }, 3000);

        // Fake donations and comments
        setInterval(() => {
            const fakeComments = [
                { user: 'viewer88', message: 'Wow, looking great!' },
                { user: 'donor99', message: 'Donated $5 - Love this!', isDonation: true },
                { user: 'fanGirl22', message: 'This is awesome!' },
            ];

            const randomComment = fakeComments[Math.floor(Math.random() * fakeComments.length)];
            const newMessage = document.createElement('div');
            newMessage.classList.add('message');
            if (randomComment.isDonation) newMessage.classList.add('donation');

            newMessage.innerHTML = `<span>${randomComment.user}:</span> ${randomComment.message}`;
            messages.appendChild(newMessage);
            messages.scrollTop = messages.scrollHeight;
        }, 5000);

        // Allow users to add messages
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
    </script>
</body>
</html>
