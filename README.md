<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Bouncing Block Screensaver</title>
  <style>
    body {
      margin: 0;
      overflow: hidden;
      background-color: black;
    }

    #block {
      width: 50px;
      height: 50px;
      background-color: red;
      position: absolute;
      border-radius: 5px;
    }
  </style>
</head>
<body>
  <div id="block"></div>

  <script>
    const block = document.getElementById("block");

    let posX = Math.random() * window.innerWidth;
    let posY = Math.random() * window.innerHeight;
    let speedX = 2 + Math.random() * 3; // Speed in the X direction
    let speedY = 2 + Math.random() * 3; // Speed in the Y direction

    function updatePosition() {
      posX += speedX;
      posY += speedY;

      // Bounce off the walls
      if (posX + block.offsetWidth >= window.innerWidth || posX <= 0) {
        speedX *= -1;
      }

      if (posY + block.offsetHeight >= window.innerHeight || posY <= 0) {
        speedY *= -1;
      }

      block.style.left = `${posX}px`;
      block.style.top = `${posY}px`;

      requestAnimationFrame(updatePosition);
    }

    updatePosition();

    // Adjust position on window resize
    window.addEventListener("resize", () => {
      posX = Math.min(posX, window.innerWidth - block.offsetWidth);
      posY = Math.min(posY, window.innerHeight - block.offsetHeight);
    });
  </script>
</body>
</html>
