<!DOCTYPE html>
<html lang="th">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>แมวส้มขนสั่น (เวอร์ชันปุ่ม)</title>
<style>
  body {
    background-color: #fff5e6;
    text-align: center;
    font-family: 'Comic Sans MS', cursive, sans-serif;
    margin-top: 60px;
  }
  h1 {
    color: #ff6600;
  }
  button {
    font-size: 2em;
    background-color: #ff9966;
    border: none;
    border-radius: 15px;
    padding: 20px 40px;
    cursor: pointer;
    box-shadow: 0 4px 6px rgba(0,0,0,0.2);
    transition: transform 0.2s ease;
    position: relative;
    user-select: none;
  }
  button:active {
    transform: scale(0.9);
  }
  .message {
    font-size: 1.5em;
    color: #ff6600;
    margin-top: 30px;
    height: 2em;
  }
  .counter {
    font-size: 1.2em;
    margin-top: 10px;
    color: #ff9966;
  }
  .heart {
    position: absolute;
    font-size: 2em;
    animation: floatUp 1s ease forwards;
    pointer-events: none;
  }
  @keyframes floatUp {
    0% { transform: translateY(0); opacity: 1; }
    100% { transform: translateY(-100px); opacity: 0; }
  }
</style>
</head>
<body>

<h1>🐾 แมวส้มขนสั่น 🐾</h1>
<button id="loveBtn">กดที่นี่</button>
<div class="message" id="message"></div>
<div class="counter" id="counter">กดแล้ว: 0 ครั้ง</div>

<audio id="meow-sound" src="https://www.fesliyanstudios.com/play-mp3/387" preload="auto"></audio>

<script>
  const messages = [
    "รักนะครับ ❤️",
    "คิดถึงจังครับ 🐾",
    "น่ารักจังเลย 😻",
    "จุ๊บๆ นะครับ 💋"
  ];

  let clickCount = 0;
  const loveBtn = document.getElementById("loveBtn");
  const message = document.getElementById("message");
  const counter = document.getElementById("counter");
  const meowSound = document.getElementById("meow-sound");

  loveBtn.addEventListener("click", (event) => {
    clickCount++;
    const randomMessage = messages[Math.floor(Math.random() * messages.length)];
    message.textContent = randomMessage;
    counter.textContent = `กดแล้ว: ${clickCount} ครั้ง`;

    // เล่นเสียงแมว
    meowSound.currentTime = 0;
    meowSound.play();

    // สร้างหัวใจลอย
    const heart = document.createElement("div");
    heart.textContent = "❤️";
    heart.className = "heart";
    heart.style.left = (event.clientX - loveBtn.offsetLeft - 15) + "px";
    heart.style.top = (event.clientY - loveBtn.offsetTop - 40) + "px";
    loveBtn.appendChild(heart);

    setTimeout(() => {
      heart.remove();
    }, 1000);
  });
</script>

</body>
</html>
