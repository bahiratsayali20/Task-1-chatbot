<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Rule-Based Chatbot</title>
  <style>
    body { font-family: Arial, sans-serif; background: #f4f4f9; display: flex; justify-content: center; padding: 40px; }
    .chat-container { width: 400px; background: #fff; padding: 20px; border-radius: 12px; box-shadow: 0 4px 10px rgba(0,0,0,0.1); }
    .chat-box { height: 300px; overflow-y: auto; border: 1px solid #ccc; padding: 10px; margin-bottom: 10px; border-radius: 8px; background: #fafafa; }
    .message { margin: 5px 0; }
    .user { color: blue; }
    .bot { color: green; }
    input[type="text"] { width: 75%; padding: 8px; border: 1px solid #ccc; border-radius: 6px; }
    button { padding: 8px 12px; background: #4CAF50; color: white; border: none; border-radius: 6px; cursor: pointer; }
    button:hover { background: #45a049; }
  </style>
</head>
<body>
  <div class="chat-container">
    <h2>Rule-Based Chatbot 🤖</h2>
    <div class="chat-box" id="chatBox"></div>
    <input type="text" id="userInput" placeholder="Type a message..." />
    <button onclick="sendMessage()">Send</button>
  </div>

  <script>
    function sendMessage() {
      let inputField = document.getElementById("userInput");
      let userText = inputField.value.trim();
      if (userText === "") return;

      appendMessage("You", userText, "user");
      inputField.value = "";

      // Rule-based responses
      let botResponse = "";
      let text = userText.toLowerCase();

      if (["bye", "exit", "quit"].includes(text)) {
        botResponse = "Goodbye! Have a nice day 😊";
      } else if (text.includes("hello") || text.includes("hi")) {
        botResponse = "Hello there! How can I help you today?";
      } else if (text.includes("how are you")) {
        botResponse = "I'm just a program, but I'm doing great! How about you?";
      } else if (text.includes("your name")) {
        botResponse = "I'm a simple rule-based chatbot 🤖";
      } else if (text.includes("weather")) {
        botResponse = "I can't check the weather right now, but I hope it's nice where you are!";
      } else if (text.includes("time")) {
        let now = new Date().toLocaleTimeString();
        botResponse = "The current time is " + now;
      } else {
        botResponse = "Sorry, I don’t understand that. Can you try rephrasing?";
      }

      appendMessage("Chatbot", botResponse, "bot");
    }

    function appendMessage(sender, message, className) {
      let chatBox = document.getElementById("chatBox");
      let messageElement = document.createElement("div");
      messageElement.className = "message " + className;
      messageElement.textContent = sender + ": " + message;
      chatBox.appendChild(messageElement);
      chatBox.scrollTop = chatBox.scrollHeight;
    }
  </script>
</body>
</html>
