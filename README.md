<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Live Chat Mock-Up</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #1a1a1a;
            color: #fff;
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
            display: flex;
            justify-content: center;
            gap: 15px;
            padding: 10px 0;
            background: #444;
        }
        nav a {
            color: #ff69b4;
            text-decoration: none;
            font-size: 1.2em;
        }
        nav a:hover {
            text-decoration: underline;
        }
        .main-container {
            display: grid;
            grid-template-columns: 1fr;
            gap: 20px;
            padding: 20px;
        }
        .live-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 15px;
        }
        .live-box {
            background: #2c2c2c;
            padding: 15px;
            border-radius: 8px;
            text-align: center;
        }
        .live-box img {
            width: 100%;
            border-radius: 8px;
            margin-bottom: 10px;
        }
        .live-box .username {
            font-size: 1.1em;
            font-weight: bold;
        }
        .chat-container {
            background: #2c2c2c;
            border-radius: 8px;
            padding: 20px;
            text-align: center;
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
            text-align: left;
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
        <h1>Live Chat Mock-Up</h1>
    </header>
    <nav>
        <a href="#home">Home</a>
        <a href="#live">Go Live</a>
        <a href="#settings">Settings</a>
    </nav>
    <div class="main-container" id="home">
        <h2>Welcome to Live Chat</h2>
        <p>Explore live streams or start your own broadcast!</p>
        <div class="live-grid">
            <div class="live-box">
                <img src="https://via.placeholder.com/300x200" alt="Live Stream">
                <p class="username">User123</p>
            </div>
            <div class="live-box">
                <img src="https://via.placeholder.com/300x200" alt="Live Stream">
                <p class="username">Streamer456</p>
            </div>
        </div>
    </div>
    <div class="main-container" id="live">
        <div class="chat-container">
            <div class="viewer-count">Viewers: <span id="viewerCount">75</span></div>
            <div class="messages" id="messages">
                <div class="message"><span>User789:</span> Wow, nice setup!</div>
            </div>
            <div class="fake-input">
                <input type="text" id="userMessage" placeholder="Type your message...">
                <button onclick="sendMessage()">Send</button>
            </div>
        </div>
    </div>
    <script>
        const messages = document.getElementById('messages');
        const viewerCount = document.getElementById('viewerCount');

        // Simulate slow fluctuating viewer count
        setInterval(() => {
            const viewers = Math.random() > 0.5 ? viewerCount.textContent++ : viewerCount.textContent--;
        }, 5000);

        // Simulated random chat messages
        const randomMessages = [
            "Pull it out",
            "mmmm",
            "I like ur arms",
            "hi",
            "dhdhshsshfskskajkak",
            "where are you located?",
            "can you d",
            "Do you prefer morf",
            "secxcxcx",
            "xoxo",
            "wowwwwwa",
            "holyshit",
            "yes."
        ];

        setInterval(() => {
            const newMessage = document.createElement('div');
            newMessage.classList.add('message');
            newMessage.innerHTML = `<span>User${Math.floor(Math.random() * 1000)}:</span> ${randomMessages[Math.floor(Math.random() * randomMessages.length)]}`;
            messages.appendChild(newMessage);
            messages.scrollTop = messages.scrollHeight;
        }, 182000); // 3 minutes 2 seconds

        // Simulated donations
        const donationMessages = [
            "where are you located?",
            "I'm hungry for you",
            "Do you do private chats?"
        ];

        let donationIndex = 0;
        setInterval(() => {
            const newDonation = document.createElement('div');
            newDonation.classList.add('message', 'donation');
            newDonation.innerHTML = `<span>Donor1:</span> ${donationMessages[donationIndex]}`;
            messages.appendChild(newDonation);
            messages.scrollTop = messages.scrollHeight;

            donationIndex = (donationIndex + 1) % donationMessages.length;
        }, 360000); // 6 minutes

        // Allow users to send messages
        function sendMessage() {
            const userMessage = document.getElementById('userMessage').value;
            if (!userMessage) return;

            const newMessage = document.createElement('div');
            newMessage.classList.add('message');
            newMessage.innerHTML = `<span>You:</span> ${userMessage}`;
            messages.appendChild(newMessage);
            messages.scrollTop = messages.scrollHeight;
        }
    </script>
</body>
</html>
