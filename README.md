# Aviator-Predictor-V3-
<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Aviator Predictor (Demo)</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #111;
      color: #fff;
      text-align: center;
      padding: 2rem;
    }
    .predictor-box {
      background: #222;
      border-radius: 10px;
      padding: 2rem;
      max-width: 400px;
      margin: 0 auto;
    }
    button {
      padding: 10px 20px;
      background: #f44336;
      border: none;
      color: white;
      border-radius: 5px;
      cursor: pointer;
      margin-top: 1rem;
    }
    .toggle {
      margin-top: 1rem;
    }
    .prediction {
      font-size: 2rem;
      margin-top: 1rem;
      color: #4caf50;
    }
    .history {
      margin-top: 2rem;
      text-align: left;
      background: #333;
      padding: 1rem;
      border-radius: 10px;
      max-height: 200px;
      overflow-y: auto;
    }
    .history-entry {
      margin-bottom: 0.5rem;
      border-bottom: 1px solid #444;
      padding-bottom: 0.25rem;
    }
  </style>
</head>
<body>
  <div class="predictor-box">
    <h1>Aviator Predictor (AI-Demo)</h1>
    <p>Click below to predict the next multiplier:</p>
    <div class="toggle">
      <label>
        <input type="checkbox" id="modeToggle" /> Realistic Mode
      </label>
    </div>
    <button onclick="predict()">Predict</button>
    <div class="prediction" id="prediction">--</div><div class="history" id="history">
  <h3>Prediction History</h3>
</div>

  </div>  <script>
    const historyContainer = document.getElementById('history');

    function predict() {
      const isRealMode = document.getElementById('modeToggle').checked;
      let prediction;

      if (isRealMode) {
        // Realistic mode (random between 1.00x to 10.00x, evenly distributed)
        prediction = (Math.random() * 9 + 1).toFixed(2);
      } else {
        // Biased mode (70% chance of high win)
        const highWins = [5.00, 8.50, 12.00, 20.00, 25.00, 33.33, 50.00, 75.00, 100.00];
        const randomChance = Math.random();

        if (randomChance > 0.3) {
          prediction = highWins[Math.floor(Math.random() * highWins.length)].toFixed(2);
        } else {
          prediction = (Math.random() * 3.99 + 1).toFixed(2);
        }
      }

      document.getElementById('prediction').textContent = prediction + 'x';
      addToHistory(prediction + 'x');
    }

    function addToHistory(value) {
      const entry = document.createElement('div');
      entry.className = 'history-entry';
      entry.textContent = `Prediction: ${value}`;
      historyContainer.appendChild(entry);
    }
  </script></body>
</html>
