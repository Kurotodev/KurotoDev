<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Rotating Circle Canvas</title>
  <style>
    body {
      background-color: #0d1117;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
    }
    canvas {
      border-radius: 8px;
    }
  </style>
</head>
<body>

<canvas id="canvas" width="300" height="300"></canvas>

<script>
  const canvas = document.getElementById('canvas');
  const ctx = canvas.getContext('2d');

  let angle = 0;

  function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);

    const centerX = canvas.width / 2;
    const centerY = canvas.height / 2;
    const radius = 80;

    ctx.save();
    ctx.translate(centerX, centerY);
    ctx.rotate(angle);

    // Círculo base
    ctx.beginPath();
    ctx.arc(0, 0, radius, 0, Math.PI * 2);
    ctx.strokeStyle = '#58a6ff';
    ctx.lineWidth = 6;
    ctx.stroke();

    // Indicador de rotación (Punto orbital)
    ctx.beginPath();
    ctx.arc(radius, 0, 10, 0, Math.PI * 2);
    ctx.fillStyle = '#238636';
    ctx.fill();

    ctx.restore();

    angle += 0.05;
    requestAnimationFrame(draw);
  }

  draw();
</script>

</body>
</html>
