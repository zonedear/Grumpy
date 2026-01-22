<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Grumpy Rank</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f0f0f0;
      text-align: center;
      padding: 40px;
      transition: background 0.3s;
    }

    .box {
      background: white;
      padding: 20px;
      border-radius: 14px;
      max-width: 360px;
      margin: auto;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
    }

    button, a {
      margin-top: 12px;
      padding: 10px 16px;
      border-radius: 8px;
      border: none;
      background: #333;
      color: white;
      text-decoration: none;
      cursor: pointer;
      display: inline-block;
    }

    input[type="range"] {
      width: 100%;
    }

    #quote {
      margin-top: 14px;
      font-style: italic;
    }
  </style>
</head>

<body>
  <div class="box">
    <h2>Grumpy Rank 😐</h2>

    <input type="range" min="1" max="10" value="5" id="rank">
    <p>Rank: <span id="value">5</span></p>

    <button id="checkBtn">Check Mood</button>

    <p id="result"></p>
    <p id="quote"></p>

    <a id="coffeeBtn"
       href="https://www.google.com/maps/search/cafe+near+me"
       target="_blank"
       style="display:none;">
       ☕ Go get coffee
    </a>
  </div>

  <script>
    const rank = document.getElementById("rank");
    const value = document.getElementById("value");
    const result = document.getElementById("result");
    const quote = document.getElementById("quote");
    const coffeeBtn = document.getElementById("coffeeBtn");
    const checkBtn = document.getElementById("checkBtn");

    const quotes = [
      "You’re doing better than you think.",
      "It’s okay to take a break.",
      "Coffee helps more than expected ☕",
      "Breathe. You’ve got this.",
      "Every mood is temporary."
    ];

    rank.addEventListener("input", () => {
      value.textContent = rank.value;
    });

    checkBtn.addEventListener("click", () => {
      const r = Number(rank.value);
      coffeeBtn.style.display = "none";

      if (r <= 2) {
        document.body.style.background = "#FFF4CC";
        result.textContent = "😄 Super good mood! You should meet Danattha 💛";
      } else if (r <= 4) {
        document.body.style.background = "#E6F7FF";
        result.textContent = "😊 Feeling good today!";
      } else if (r <= 6) {
        document.body.style.background = "#EEEEEE";
        result.textContent = "😐 Neutral mood. Take it easy.";
      } else if (r <= 8) {
        document.body.style.background = "#FFE6E6";
        result.textContent = "😠 Getting grumpy. Coffee might help ☕";
        coffeeBtn.style.display = "inline-block";
      } else {
        document.body.style.background = "#FFCCCC";
        result.textContent = "😤 Very grumpy! Coffee + rest ASAP!";
        coffeeBtn.style.display = "inline-block";
      }

      const random = Math.floor(Math.random() * quotes.length);
      quote.textContent = `"${quotes[random]}"`;
    });
  </script>
</body>
</html>
