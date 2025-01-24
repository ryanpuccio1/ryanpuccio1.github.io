<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Chatxo Live</title>
    <style>
        body {
            margin: 0;
            font-family: Arial, sans-serif;
            background-color: #1a1a1a;
            color: white;
        }
        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            background-color: #333;
            padding: 10px 20px;
        }
        header h1 {
            color: #ff69b4;
            font-size: 1.8em;
            margin: 0;
        }
        header nav {
            display: flex;
            gap: 15px;
        }
        header nav a {
            color: white;
            text-decoration: none;
            font-size: 1em;
            padding: 5px 10px;
            border-radius: 5px;
        }
        header nav a:hover {
            background-color: #ff69b4;
            color: white;
        }
        .hero {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            padding: 20px;
            background-color: #2c2c2c;
        }
        .hero img {
            max-width: 200px;
            height: auto;
            margin: 10px;
            border-radius: 10px;
            border: 2px solid #444;
        }
        .chat-section {
            display: flex;
            flex-direction: column;
            align-items: center;
            margin: 20px auto;
            max-width: 1000px;
            background-color: #2c2c2c;
            border-radius: 8px;
            padding: 20px;
        }
        .viewer-count {
            margin-bottom: 10px;
            font-size: 1.2em;
        }
        .messages {
            width: 100%;
            height: 300px;
            overflow-y: auto;
            border: 1px solid #444;
            padding: 10px;
            border-radius: 4px;
            background: #1e1e1e;
            margin-bottom: 10px;
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
            width: 100%;
        }
        .fake-input input {
            flex: 1;
            padding: 10px;
            border: 1px solid #444;
            border-radius: 4px;
            background: #1e1e1e;
            color: white;
            margin-right: 10px;
        }
        .fake-input button {
            padding: 10px 20px;
            border: none;
            border-radius: 4px;
            background: #ff69b4;
            color: white;
            cursor: pointer;
        }
        .fake-input button:hover {
            background: #e04898;
        }
        footer {
            text-align: center;
            padding: 10px;
            background-color: #333;
            color: white;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <header>
        <h1>Chatxo Live</h1>
        <nav>
            <a href="#">Home</a>
            <a href="#">Go Live</a>
            <a href="#">Settings</a>
            <a href="#">Profile</a>
        </nav>
    </header>

    <div class="hero">
        <img src="https://via.placeholder.com/200" alt="Live Chat 1">
        <img src="https://via.placeholder.com/200" alt="Live Chat 2">
        <img src="https://via.placeholder.com/200" alt="Live Chat 3">
        <img src="https://via.placeholder.com/200" alt="Live Chat 4">
    </div>

    <div class="chat-section">
        <div class="viewer-count">Viewers: <span id="viewerCount">72</span></div>
        <div class="messages" id="messages">
            <div class="message"><span>user123:</span> You're doing great!</div>
            <div class="message donation"><span>donor99:</span> Donated $10 - Keep it up!</div>
        </div>
        <div class="fake-input">
            <input type="text" id="userMessage" placeholder="Type your message...">
            <button onclick="sendMessage()">Send</button>
        </div>
    </div>

    <footer>
        &copy; 2025 Chatxo. All rights reserved.
    </footer>

    <script>
        const messages = document.getElementById('messages');
        const viewerCount = document.getElementById('viewerCount');

        // Viewer count fluctuation logic
        setInterval(() => {
            const change = Math.random() > 0.5 ? 1 : -1;
            const currentCount = parseInt(viewerCount.textContent);
            const newCount = Math.max(68, Math.min(80, currentCount + change));
            viewerCount.textContent = newCount;
        }, 4000);

        // Fake messages
        setInterval(() => {
            if (Math.random() > 0.3) {
                const fakeMessages = [
                    { user: 'viewer42', message: 'Looking awesome!' },
                    { user: 'donor88', message: 'Donated $5 - Keep going!', isDonation: true },
                    { user: 'fanGirl22', message: 'Love this stream!' },
                ];

                const randomMessage = fakeMessages[Math.floor(Math.random() * fakeMessages.length)];
                const newMessage = document.createElement('div');
                newMessage.classList.add('message');
                if (randomMessage.isDonation) newMessage.classList.add('donation');
                newMessage.innerHTML = `<span>${randomMessage.user}:</span> ${randomMessage.message}`;
                messages.appendChild(newMessage);
                messages.scrollTop = messages.scrollHeight;
            }
        }, 5000);

        // User message
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
