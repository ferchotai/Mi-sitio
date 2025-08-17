# Mi-sitio
Opcional 
<!doctype html>
<html>
  <head>
    <title></title>
    <link rel="stylesheet" href="style.css">
  </head>
  <body>
    <script src="script.js"></script>
  </body>
</html>
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>¿Eres Manuel?</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      background: linear-gradient(to bottom right, #ffd6eb, #ffb3d9);
      font-family: 'Comic Sans MS', cursive, sans-serif;
      text-align: center;
      overflow: hidden;
    }
    .container {
      background: white;
      padding: 40px;
      border-radius: 20px;
      box-shadow: 0px 6px 20px rgba(0,0,0,0.2);
      position: relative;
      z-index: 2;
    }
    h1 {
      margin-bottom: 20px;
      font-size: 30px;
      color: #d63384;
    }
    p {
      margin-bottom: 30px;
      font-size: 20px;
      color: #444;
    }
    .buttons {
      display: flex;
      justify-content: center;
      gap: 25px;
    }
    button {
      padding: 15px 30px;
      font-size: 18px;
      border: none;
      border-radius: 50px;
      cursor: pointer;
      transition: transform 0.2s, background-color 0.3s;
    }
    .yes {
      background-color: #ff69b4;
      color: white;
    }
    .yes:hover {
      background-color: #ff85c1;
      transform: scale(1.1);
    }
    .no {
      background-color: #f5426c;
      color: white;
    }
    .no:hover {
      background-color: #ff5c85;
      transform: scale(1.1);
    }

    /* Globitos */
    .balloon {
      position: absolute;
      width: 25px;
      height: 35px;
      background: pink;
      border-radius: 50% 50% 50% 50% / 60% 60% 40% 40%;
      animation: float 6s linear infinite;
      z-index: 1;
    }
    @keyframes float {
      0% { transform: translateY(-100vh) scale(1); opacity: 1; }
      100% { transform: translateY(100vh) scale(0.8); opacity: 0; }
    }

    /* Pastelito */
    .cake {
      font-size: 50px;
      margin-top: 20px;
      animation: bounce 1s infinite alternate;
    }
    @keyframes bounce {
      0% { transform: translateY(0); }
      100% { transform: translateY(-15px); }
    }

    /* Botón cuenta regresiva */
    .countdown-btn {
      margin-top: 20px;
      padding: 12px 25px;
      font-size: 18px;
      border-radius: 30px;
      border: none;
      background-color: #ff69b4;
      color: white;
      cursor: pointer;
      transition: transform 0.2s, background-color 0.3s;
    }
    .countdown-btn:hover {
      background-color: #ff85c1;
      transform: scale(1.1);
    }
    #countdown-timer {
      margin-top: 15px;
      font-size: 22px;
      color: #d63384;
    }
  </style>
</head>
<body>
  <!-- Globitos -->
  <div class="balloon" style="left:10%; animation-delay:0s;"></div>
  <div class="balloon" style="left:30%; background:#ff8fab; animation-delay:2s;"></div>
  <div class="balloon" style="left:50%; background:#fbb1bd; animation-delay:4s;"></div>
  <div class="balloon" style="left:70%; background:#ff94c2; animation-delay:1s;"></div>
  <div class="balloon" style="left:90%; background:#ffa6d1; animation-delay:3s;"></div>

  <div class="container" id="content">
    <h1>¿Eres Manuel?</h1>
    <p id="mensaje">Hola, si eres Manuel presiona SI, de lo contrario presiona NO :)</p>
    <div class="buttons">
      <button class="yes" onclick="sayYes()">SI</button>
      <button class="no" onclick="sayNo()">NO</button>
    </div>
  </div>

  <script>
    let noClicks = 0;

    function sayYes() {
      document.getElementById("content").innerHTML = `
        <h1>🎉 Feliz cumple Manuelito 🎂🥳</h1>
        <p>Te mereces lo mejor del mundo, que tengas bonito día y un añito más de vida porque ya estás viejito felices 21 😊❤️</p>
        <div class="cake">🍰</div>
        <p>¿Quieres saber cuánto falta para tu próximo cumple número 22? 🎈</p>
        <div class="buttons">
          <button class="yes" onclick="showCountdown()">SI</button>
          <button class="no" onclick="doNothing()">NO</button>
        </div>
        <h2 id="countdown-timer"></h2>
      `;
    }

    function sayNo() {
      noClicks++;
      let mensajes = [
        "¿Seguro? 🤔",
        "¿Segurito? 😺",
        "Si eres Manuel",
        "No te creo... 🙄",
        "¡Mentirosooo! 😓",
        "Ponle que SÍ porfis 🥺"
      ];
      if (noClicks <= mensajes.length) {
        document.getElementById("mensaje").innerText = mensajes[noClicks - 1];
      }
    }

    function doNothing() {
      // El botón NO en la segunda etapa no hace nada
    }

    function showCountdown() {
      const countdownTimer = document.getElementById("countdown-timer");
      const birthday = new Date("August 21, 2026 00:00:00");
      // Ocultamos los botones SI/NO de la segunda etapa
      const buttons = document.querySelectorAll(".buttons button");
      buttons.forEach(btn => btn.style.display = "none");

      const interval = setInterval(() => {
        const now = new Date();
        const diff = birthday - now;

        if (diff <= 0) {
          countdownTimer.innerText = "¡Es hoy! 🎂🥳 ¡Feliz cumpleaños Manuelito!";
          clearInterval(interval);
        } else {
          const days = Math.floor(diff / (1000 * 60 * 60 * 24));
          const hours = Math.floor((diff / (1000 * 60 * 60)) % 24);
          const minutes = Math.floor((diff / (1000 * 60)) % 60);
          const seconds = Math.floor((diff / 1000) % 60);

          countdownTimer.innerText = `${days} días ${hours}h ${minutes}m ${seconds}s`;
        }
      }, 1000);
    }
  </script>
</body>
</html>
