<!DOCTYPE html>
<html>
<head>
  <title>Exploding Text Easter Egg</title>
  <style>
    body {
      margin: 0;
      background: #000;
      font-family: monospace;
      overflow: hidden;
    }

    #explodeText {
      position: absolute;
      top: 40%;
      left: 50%;
      transform: translate(-50%, -50%);
      font-size: 50px;
      color: #00ffff;
      cursor: pointer;
      user-select: none;
      z-index: 2;
    }

    #easterEggMessage {
      position: absolute;
      top: 55%;
      left: 50%;
      transform: translate(-50%, -50%);
      font-size: 24px;
      color: #00ffaa;
      text-align: center;
      opacity: 0;
      transition: opacity 1.5s ease;
      z-index: 2;
    }

    canvas {
      position: fixed;
      top: 0;
      left: 0;
      z-index: 1;
    }
  </style>
</head>
<body>

  <div id="explodeText">Tap to Initiate 💣</div>
  <div id="easterEggMessage">Access Granted<br>Welcome, Agent 042 🕵️‍♂️</div>
  <canvas id="canvas"></canvas>

  <script>
    const canvas = document.getElementById('canvas');
    const ctx = canvas.getContext('2d');
    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const particles = [];
    const colors = ['#00ffee', '#33ffcc', '#00ccff', '#00ff99', '#66ffee'];

    class Particle {
      constructor(x, y) {
        this.x = x;
        this.y = y;
        this.radius = Math.random() * 4 + 2;
        this.color = colors[Math.floor(Math.random() * colors.length)];
        this.velocity = {
          x: (Math.random() - 0.5) * 6,
          y: (Math.random() - 0.5) * 6
        };
        this.alpha = 1;
      }

      draw() {
        ctx.save();
        ctx.globalAlpha = this.alpha;
        ctx.beginPath();
        ctx.arc(this.x, this.y, this.radius, 0, Math.PI * 2);
        ctx.fillStyle = this.color;
        ctx.fill();
        ctx.restore();
      }

      update() {
        this.x += this.velocity.x;
        this.y += this.velocity.y;
        this.alpha -= 0.01;
      }
    }

    function animate() {
      ctx.fillStyle = 'rgba(0, 0, 0, 0.15)';
      ctx.fillRect(0, 0, canvas.width, canvas.height);
      particles.forEach((p, i) => {
        if (p.alpha <= 0) particles.splice(i, 1);
        else {
          p.update();
          p.draw();
        }
      });
      requestAnimationFrame(animate);
    }

    animate();

    const explodeText = document.getElementById('explodeText');
    const message = document.getElementById('easterEggMessage');

    explodeText.onclick = function () {
      const rect = explodeText.getBoundingClientRect();
      const centerX = rect.left + rect.width / 2;
      const centerY = rect.top + rect.height / 2;

      for (let i = 0; i < 100; i++) {
        particles.push(new Particle(centerX, centerY));
      }

      explodeText.style.display = "none";

      setTimeout(() => {
        message.style.opacity = 1;
      }, 1500);
    };

    window.onresize = () => {
      canvas.width = window.innerWidth;
      canvas.height = window.innerHeight;
    };
  </script>
</body>
</html>
