
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Be My Valentine? 💕</title>
  <style>
    body {
      background-color: #ffe6f0;
      font-family: Arial, sans-serif;
      text-align: center;
      padding-top: 100px;
      overflow: hidden;
      transition: background-color 0.5s;
    }

    h1 {
      color: #e60073;
      font-size: 3em;
      font-weight: bold;
      transition: all 1s ease;
      position: relative;
      z-index: 10;
    }

    button {
      background-color: #ff4da6;
      border: none;
      color: white;
      padding: 15px 30px;
      font-size: 1.2em;
      border-radius: 25px;
      cursor: pointer;
      margin: 10px;
      position: relative;
      z-index: 10;
    }

    button:hover {
      background-color: #cc0066;
    }

    .heart, .floatingHeart, .confetti {
      position: absolute;
      font-size: 24px;
      color: red;
      z-index: 5;
    }

    .floatingHeart {
      animation: floatDown linear infinite;
    }

    @keyframes fly {
      0% { transform: translate(0, 0) scale(1); opacity: 1; }
      100% { transform: translate(var(--x), var(--y)) scale(2); opacity: 0; }
    }

    @keyframes floatDown {
      0% { transform: translateY(-50px); opacity: 1; }
      100% { transform: translateY(110vh); opacity: 0; }
    }

    .confetti {
      font-size: 18px;
      color: hsl(var(--hue), 100%, 50%);
      animation: confettiFly 1s linear forwards;
    }

    @keyframes confettiFly {
      0% { transform: translate(0, 0) rotate(0deg); opacity: 1; }
      100% { transform: translate(var(--x), var(--y)) rotate(360deg); opacity: 0; }
    }
  </style>
</head>
<body>

  <h1>Will You Be My Valentine? 💕</h1>

  <button id="yesBtn">Yes</button>
  <button id="noBtn">No</button>

  <script>
    const yesBtn = document.getElementById('yesBtn');
    const noBtn = document.getElementById('noBtn');
    const h1 = document.querySelector('h1');

    // Floating hearts background
    function spawnFloatingHeart() {
      const heart = document.createElement('div');
      heart.className = 'floatingHeart';
      heart.textContent = '❤️';
      heart.style.left = Math.random() * window.innerWidth + 'px';
      heart.style.fontSize = (12 + Math.random() * 24) + 'px';
      heart.style.animationDuration = (3 + Math.random() * 5) + 's';
      document.body.appendChild(heart);
      setTimeout(() => heart.remove(), 8000);
    }
    setInterval(spawnFloatingHeart, 500);

    // YES button click: hearts, confetti, then text
    yesBtn.addEventListener('click', () => {
      // Explode hearts and confetti
      for (let i = 0; i < 30; i++) {
        const heart = document.createElement('div');
