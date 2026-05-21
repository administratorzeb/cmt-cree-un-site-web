<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <title>Mini Jeu en Ligne</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      text-align: center;
      background: #f4f4f9;
      margin: 0;
      padding: 0;
    }
    header {
      background: #004080;
      color: white;
      padding: 20px;
    }
    #gameArea {
      position: relative;
      width: 600px;
      height: 400px;
      margin: 30px auto;
      border: 2px solid #004080;
      background: #e0f0ff;
    }
    #square {
      position: absolute;
      width: 50px;
      height: 50px;
      background: red;
      cursor: pointer;
    }
    #score {
      font-size: 20px;
      margin-top: 10px;
      color: #004080;
    }
    button {
      padding: 10px 20px;
      margin-top: 20px;
      background: #004080;
      color: white;
      border: none;
      cursor: pointer;
    }
    button:hover {
      background: #0066cc;
    }
  </style>
</head>
<body>
  <header>
    <h1>Mini Jeu : Clique sur le carré</h1>
    <p>Essaye de cliquer sur le carré rouge pour gagner des points !</p>
  </header>

  <div id="gameArea">
    <div id="square"></div>
  </div>

  <div id="score">Score : 0</div>
  <button onclick="startGame()">Rejouer</button>

  <script>
    let score = 0;
    const square = document.getElementById("square");
    const gameArea = document.getElementById("gameArea");
    const scoreDisplay = document.getElementById("score");

    function randomPosition() {
      const maxX = gameArea.clientWidth - square.clientWidth;
      const maxY = gameArea.clientHeight - square.clientHeight;
      const x = Math.floor(Math.random() * maxX);
      const y = Math.floor(Math.random() * maxY);
      square.style.left = x + "px";
      square.style.top = y + "px";
    }

    square.addEventListener("click", () => {
      score++;
      scoreDisplay.textContent = "Score : " + score;
      randomPosition();
    });

    function startGame() {
      score = 0;
      scoreDisplay.textContent = "Score : " + score;
      randomPosition();
    }

    // Lancer le jeu au chargement
    window.onload = startGame;
  </script>
</body>
</html>
