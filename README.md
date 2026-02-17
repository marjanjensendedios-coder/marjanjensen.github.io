<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Push Me 🌸</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      height: 100vh;
      background: #fff0f5;
      font-family: system-ui, sans-serif;
      overflow: hidden;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      position: relative;
    }

    button {
      padding: 18px 48px;
      font-size: 1.8rem;
      font-weight: bold;
      color: white;
      background: #ff6bcb;
      border: none;
      border-radius: 50px;
      box-shadow: 0 8px 25px rgba(255, 105, 180, 0.4);
      cursor: pointer;
      transition: all 0.3s;
      z-index: 100;
    }

    button:hover {
      transform: translateY(-4px) scale(1.08);
      background: #ff85c0;
      box-shadow: 0 12px 35px rgba(255, 105, 180, 0.55);
    }

    button:active {
      transform: translateY(2px) scale(0.96);
    }

    .flower {
      position: absolute;
      font-size: 2.5rem;
      pointer-events: none;
      user-select: none;
      animation: fall linear forwards;
      z-index: 10;
    }

    .message {
      position: absolute;
      font-size: 4.8rem;
      font-weight: bold;
      color: #ff1493;
      text-shadow: 0 0 20px rgba(255, 20, 147, 0.6);
      opacity: 0;
      transform: scale(0.6);
      transition: all 1.2s ease-out;
      pointer-events: none;
      z-index: 50;
      text-align: center;
      max-width: 90%;
      line-height: 1.1;
    }

    .message.show {
      opacity: 1;
      transform: scale(1);
    }

    @keyframes fall {
      to {
        transform: translateY(120vh) rotate(720deg);
      }
    }
  </style>
</head>
<body>

  <button id="pushBtn">Push Me 🌷</button>
  <div id="message" class="message">Have a great day<br>ate Ellen! 😊</div>

  <script>
    const btn = document.getElementById('pushBtn');
    const message = document.getElementById('message');

    const flowers = ['🌸','🌺','🌼','🌻','🌷','💐','🏵️','🌹','🥀','💮','🍀','🌿'];

    function createFlower() {
      const flower = document.createElement('div');
      flower.className = 'flower';
      flower.textContent = flowers[Math.floor(Math.random() * flowers.length)];
      
      const size = Math.random() * 1.2 + 1.8;
      flower.style.fontSize = size + 'rem';
      flower.style.left = Math.random() * 100 + 'vw';
      flower.style.top = '-10vh';
      
      const duration = Math.random() * 3 + 3;
      flower.style.animationDuration = duration + 's';
      flower.style.animationDelay = Math.random() * 0.6 + 's';

      document.body.appendChild(flower);

      setTimeout(() => flower.remove(), duration * 1000 + 1000);
    }

    btn.addEventListener('click', () => {
      btn.disabled = true;
      btn.style.opacity = '0.6';

      const flowerCount = 80;
      for (let i = 0; i < flowerCount; i++) {
        setTimeout(createFlower, i * 40);
      }

      setTimeout(() => {
        message.classList.add('show');
      }, 3000);

      setTimeout(() => {
        message.classList.remove('show');
        btn.disabled = false;
        btn.style.opacity = '1';
      }, 9000);
    });
  </script>

</body>
</html>
