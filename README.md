<!DOCTYPE html>
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
      font-weight: bold; /* makes text bold */
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
    }
    button:hover {
      background-color: #cc0066;
    }
    .heart {
      position: absolute;
      font-size: 24px;
      color: red;
      animation: fly 1s linear forwards;
    }
    @keyframes fly {
      0% { transform: translate(0, 0) scale(1); opacity: 1; }
      100% { transform: translate(var(--x), var(--y)) scale(2); opacity: 0; }
    }
    #cupid {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      font-size: 5em;
      display: none;
    }
    #cupidMessage {
      position: fixed;
      top: 70%;
      left: 50%;
      transform: translateX(-50%);
      font-size: 2em;
      color: white;
      display: none;
    }
  </style>
</head>
<body>

  <h1>Will You Be My Valentine? 💕</h1>

  <button id="yesBtn">Yes</button>
  <button id="noBtn">No</button>

  <div id="cupid">💘</div>
  <div id="cupidMessage">Let's try that again! 💖</div>

  <script>
    const yesBtn = document.getElementById('yesBtn');
    const noBtn = document.getElementById('noBtn');
    let noAttempts = 0;

    // YES button hearts
    yesBtn.addEventListener('click', () => {
      for (let i = 0; i < 30; i++) {
        const heart = document.createElement('div');
        heart.className = 'heart';
        heart.textContent = '❤️';
        heart.style.left = yesBtn.offsetLeft + yesBtn.offsetWidth/2 + 'px';
        heart.style.top = yesBtn.offsetTop + yesBtn.offsetHeight/2 + 'px';

        const x = (Math.random() - 0.5) * 400 + 'px';
        const y = (Math.random() - 0.5) * 400 + 'px';
        heart.style.setProperty('--x', x);
        heart.style.setProperty('--y', y);

        document.body.appendChild(heart);
        setTimeout(() => heart.remove(), 1000);
      }

      document.querySelector('h1').textContent = "You kinda like me, huh? 💕";
    });

    // NO button runs away
    noBtn.addEventListener('mousemove', () => {
      noAttempts++;
      if (noAttempts < 3) {
        const x = Math.random() * (window.innerWidth - noBtn.offsetWidth);
        const y = Math.random() * (window.innerHeight - noBtn.offsetHeight);
        noBtn.style.position = 'absolute';
        noBtn.style.left = x + 'px';
        noBtn.style.top = y + 'px';
      } else {
        // 3rd attempt triggers cupid
        document.body.style.backgroundColor = 'black';
        noBtn.style.display = 'none';
        yesBtn.style.display = 'none';
        document.querySelector('h1').style.color = 'white';
        const cupid = document.getElementById('cupid');
        const msg = document.getElementById('cupidMessage');
        cupid.style.display = 'block';
        msg.style.display = 'block';
      }
    });
  </script>

</body>
</html>
