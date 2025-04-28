# Poleth
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Contador de Amor</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <style>
    body {
      margin: 0;
      padding: 0;
      background: url('https://blob.lacaderadeeva.com/images/2025/01/07/flow-focus-min0.27-0.43-1260-1050.jpg') no-repeat center center fixed;
      background-size: cover;
      font-family: 'Georgia', serif;
      color: white;
      overflow-x: hidden;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      text-align: center;
      padding: 20px;
      box-sizing: border-box;
      position: relative;
    }

    h1, p, .counter {
      z-index: 2;
      position: relative;
    }

    h1 {
      font-size: 26px;
      margin-bottom: 10px;
    }

    p {
      margin: 10px 0;
      font-size: 18px;
      white-space: pre-line;
      max-width: 800px;
    }

    .counter {
      margin-top: 20px;
      font-size: 20px;
      font-weight: bold;
      z-index: 3;
    }

    /* Imagen que cae */
    .falling-image {
      position: absolute;
      top: -50px;
      width: 50px;  /* Tamaño de la miniatura */
      height: 50px;
      animation: fall linear infinite;
      z-index: 1;
      pointer-events: none;
      opacity: 0.8;
    }

    @keyframes fall {
      0% {
        transform: translateY(0) rotate(0deg);
      }
      100% {
        transform: translateY(100vh) rotate(360deg);
      }
    }

    audio {
      display: none;
    }

    @media (max-width: 600px) {
      h1 {
        font-size: 22px;
      }
      p {
        font-size: 16px;
      }
      .counter {
        font-size: 18px;
      }
    }
  </style>
</head>

<body>

<h1>Desde aquel instante...</h1>

<p>
Desde el ocho de marzo, en un instante florecido,  
tu mirada a la mía quedó prendida,  
un contador en mi alma nació,  
midiendo cada segundo del amor que creció.

Cincuenta días y dos horas, guardados,  
en anhelos, risas, sueños bordados.  
Cada minuto es un pétalo del amor,  
que el tiempo acrecienta sin temor.

Y seguirá marcando este latir constante,  
esperando el día en que se funden los "hasta ahora"  
en un "para siempre".  
Y el tiempo será dulce memoria,  
de un amor que nos guía hacia nuestra historia eterna.
</p>

<div class="counter">
  Tiempo juntos:<br>
  <span id="timer"></span>
</div>

<!-- Música -->
<audio id="background-music" autoplay loop>
  <source src="https://cdn.pixabay.com/audio/2023/02/06/audio_184168f94d.mp3" type="audio/mpeg">
</audio>

<script>
document.addEventListener("DOMContentLoaded", function() {
  // Música
  const music = document.getElementById('background-music');
  document.body.addEventListener('click', () => {
    if (music.paused) {
      music.play();
    }
  });

  // Contador: fecha de inicio 8 de marzo de 2025 a las 7:00 PM
  const pastDate = new Date('2025-03-08T19:00:00');

  function updateTimer() {
    const now = new Date();
    const diff = now - pastDate;

    const days = Math.floor(diff / (1000 * 60 * 60 * 24));
    const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
    const minutes = Math.floor((diff / (1000 * 60)) % 60);
    const seconds = Math.floor((diff / 1000) % 60);

    document.getElementById('timer').innerHTML =
      `${days} días ${hours} horas ${minutes} minutos ${seconds} segundos`;
  }

  setInterval(updateTimer, 1000);
  updateTimer();

  // Crear imágenes que caen
  function createFallingImage() {
    const image = document.createElement('img');
    image.className = 'falling-image';
    image.src = 'https://i.imgur.com/nNQEj6k.png';  // URL de la imagen subida a Imgur
    image.style.left = Math.random() * window.innerWidth + 'px';
    image.style.animationDuration = (4 + Math.random() * 4) + 's';

    document.body.appendChild(image);

    setTimeout(() => {
      image.remove();
    }, 10000);
  }

  setInterval(createFallingImage, 500);
});
</script>

</body>
</html>
    
