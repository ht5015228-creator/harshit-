
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Harshit AI</title>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Arial, sans-serif;
  background: #f3f5fb;
  color: #172033;
  height: 100vh;
  display: flex;
  flex-direction: column;
}

header {
  background: #ffffff;
  padding: 16px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid #ddd;
}

.logo {
  font-size: 21px;
  font-weight: bold;
  color: #5b4bdb;
}

button {
  cursor: pointer;
  border: none;
  border-radius: 10px;
  padding: 11px 14px;
  font-size: 14px;
}

#theme {
  background: #eeeaff;
}

main {
  flex: 1;
  overflow-y: auto;
  padding: 20px 14px;
  width: 100%;
  max-width: 800px;
  margin: auto;
}

.welcome {
  text-align: center;
  padding: 35px 10px 25px;
}

.robot {
  font-size: 54px;
  margin-bottom: 12px;
}

.welcome h1 {
  font-size: 30px;
  margin-bottom: 10px;
}

.welcome p {
  color: #68738a;
  line-height: 1.6;
}

.quick {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 9px;
  margin-top: 20px;
}

.quick button {
  background: white;
  border: 1px solid #ddd;
  color: #38364c;
}

#chat {
  display: flex;
  flex-direction: column;
  gap: 14px;
  padding-bottom: 20px;
}

.message {
  padding: 14px;
  border-radius: 16px;
  max-width: 90%;
  line-height: 1.6;
  white-space: pre-wrap;
  overflow-wrap: anywhere;
}

.user {
  background: #5b4bdb;
  color: white;
  align-self: flex-end;
}

.bot {
  background: white;
  border: 1px solid #e4e5ee;
  align-self: flex-start;
}

.input-area {
  padding: 12px;
  background: white;
  border-top: 1px solid #ddd;
}

.input-box {
  display: flex;
  gap: 8px;
  max-width: 800px;
  margin: auto;
}

input {
  flex: 1;
  min-width: 0;
  padding: 14px;
  border: 1px solid #d7d9e4;
  border-radius: 12px;
  font-size: 16px;
  outline-color: #5b4bdb;
}

#send {
  background: #5b4bdb;
  color: white;
  font-weight: bold;
}

#clear {
  display: block;
  margin: 10px auto 0;
  background: transparent;
  color: #666;
}

body.dark {
  background: #111827;
  color: #f8fafc;
}

body.dark header,
body.dark .input-area {
  background: #1f2937;
  border-color: #374151;
}

body.dark .bot,
body.dark .quick button {
  background: #273449;
  color: white;
  border-color: #374151;
}

body.dark input {
  background: #111827;
  color: white;
  border-color: #374151;
}

body.dark .welcome p {
  color: #cbd5e1;
}

@media (max-width: 420px) {
  .welcome h1 {
    font-size: 25px;
  }

  .message {
    max-width: 96%;
  }

  #send {
    padding: 10px;
  }
}
</style>
</head>

<body>

<header>
  <div class="logo">✨ Harshit AI</div>
  <button id="theme">🌙 Theme</button>
</header>

<main id="main">
  <section class="welcome" id="welcome">
    <div class="robot">🤖</div>
    <h1>Hello, Harshit!</h1>
    <p>
      Welcome to your personal AI-style assistant.<br>
      What would you like to learn today?
    </p>

    <div class="quick">
      <button data-q="Teach me HTML basics">💻 Learn HTML</button>
      <button data-q="Give me a study tip">📚 Study tips</button>
      <button data-q="Tell me an interesting science fact">🔬 Science fact</button>
      <button data-q="Give me a motivational quote">🚀 Motivation</button>
    </div>
  </section>

  <section id="chat"></section>
</main>

<section class="input-area">
  <div class="input-box">
    <input id="prompt" type="text"
      placeholder="Ask me anything..."
      autocomplete="off">
    <button id="send">Send ➤</button>
  </div>
  <button id="clear">Clear conversation</button>
</section>

<script>
const chat = document.getElementById("chat");
const promptBox = document.getElementById("prompt");
const welcome = document.getElementById("welcome");

function addMessage(text, type) {
  welcome.style.display = "none";

  const div = document.createElement("div");
  div.className = "message " + type;
  div.textContent = text;
  chat.appendChild(div);

  document.getElementById("main").scrollTop =
    document.getElementById("main").scrollHeight;
}

function getReply(question) {
  const q = question.toLowerCase();

  if (q.includes("hello") || q.includes("hi") ||
      q.includes("namaste")) {
    return "Hello Harshit! 😊 Main tumhara demo assistant hoon. Aaj kya seekhna chahte ho?";
  }

  if (q.includes("html")) {
    return "HTML website ka structure banata hai.\n\nExample:\n<h1>Hello World</h1>\n<p>My first website</p>\n\nHTML ke baad CSS se design aur JavaScript se interaction add karte hain.";
  }

  if (q.includes("study") || q.includes("padhai")) {
    return "📚 Study tip:\n\n1. Ek chhota target chuno.\n2. 25 minute focus se padho.\n3. 5 minute break lo.\n4. Book band karke jo yaad hai use recall karo.\n5. Galtiyon ko dobara revise karo.";
  }

  if (q.includes("science")) {
    return "🔬 Interesting fact: Light ki speed vacuum mein lagbhag 300,000 kilometres per second hoti hai!";
  }

  if (q.includes("motivation")) {
    return "🚀 Har expert kabhi beginner tha. Roz thoda seekho, practice karo aur apni progress par dhyan do!";
  }

  if (q.includes("css")) {
    return "CSS website ko style karta hai. Example:\n\nh1 {\n  color: blue;\n  font-size: 30px;\n}\n\nIsse heading ka colour blue ho jayega.";
  }

  if (q.includes("javascript") || q.includes("programming")) {
    return "JavaScript website ko interactive banata hai. Example:\n\nalert('Hello Harshit!');\n\nIs code se ek message popup hota hai.";
  }

  if (q.includes("your name") || q.includes("tumhara naam")) {
    return "Mera naam Harshit AI hai! 😊 Ye tumhari banayi hui demo assistant website hai.";
  }

  return "Tumne poochha: \"" + question + "\"\n\nMain abhi ek basic demo assistant hoon. Mere paas live AI model connect nahi hai, isliye main har sawaal ka asli AI ki tarah jawab nahi de sakta.\n\nTum HTML, CSS, JavaScript ya study tips ke baare mein poochh sakte ho!";
}

function sendMessage(text) {
  const question = (text || promptBox.value).trim();

  if (!question) {
    promptBox.focus();
    return;
  }

  addMessage(question, "user");
  promptBox.value = "";

  addMessage(getReply(question), "bot");
}

document.getElementById("send").addEventListener("click", () => {
  sendMessage();
});

promptBox.addEventListener("keydown", event => {
  if (event.key === "Enter") sendMessage();
});

document.querySelectorAll("[data-q]").forEach(button => {
  button.addEventListener("click", () => {
    sendMessage(button.dataset.q);
  });
});

document.getElementById("theme").addEventListener("click", () => {
  document.body.classList.toggle("dark");
});

document.getElementById("clear").addEventListener("click", () => {
  chat.replaceChildren();
  welcome.style.display = "block";
  promptBox.value = "";
});

</script>
</body>
</html>
