<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Средняя цена криптоактивов</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 20px;
      background-color: #f4f4f9;
    }
    h1 {
      text-align: center;
      color: #333;
    }
    .container {
      max-width: 400px;
      margin: 0 auto;
    }
    input, button {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      border: 1px solid #ccc;
      border-radius: 8px;
    }
    button {
      background-color: #007bff;
      color: white;
      cursor: pointer;
    }
    button:hover {
      background-color: #0056b3;
    }
    .result {
      margin-top: 20px;
      padding: 10px;
      background-color: #fff;
      border-radius: 8px;
      box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Средняя цена криптоактивов</h1>

    <!-- Форма для ввода данных -->
    <input type="text" id="tokenName" placeholder="Название токена (например, BTC)">
    <input type="number" id="tokenQuantity" placeholder="Количество">
    <input type="number" id="tokenPrice" placeholder="Цена покупки">
    <button onclick="addToken()">Добавить токен</button>

    <!-- Отображение результатов -->
    <div class="result">
      <p id="averagePrice"></p>
      <p id="totalQuantity"></p>
    </div>
  </div>

  <script>
    let tokens = [];

    // Добавление токена
    function addToken() {
      const tokenName = document.getElementById("tokenName").value;
      const tokenQuantity = parseFloat(document.getElementById("tokenQuantity").value);
      const tokenPrice = parseFloat(document.getElementById("tokenPrice").value);

      if (tokenName && tokenQuantity && tokenPrice) {
        tokens.push({ name: tokenName, quantity: tokenQuantity, price: tokenPrice });
        calculateAveragePrice();
        document.getElementById("tokenName").value = "";
        document.getElementById("tokenQuantity").value = "";
        document.getElementById("tokenPrice").value = "";
      } else {
        alert("Заполните все поля!");
      }
    }

    // Расчет средней цены
    function calculateAveragePrice() {
      let totalQuantity = 0;
      let totalCost = 0;

      tokens.forEach(token => {
        totalQuantity += token.quantity;
        totalCost += token.quantity * token.price;
      });

      const averagePrice = totalCost / totalQuantity;

      document.getElementById("averagePrice").textContent = `Средняя цена: ${averagePrice.toFixed(2)} USD`;
      document.getElementById("totalQuantity").textContent = `Общее количество: ${totalQuantity}`;
    }
  </script>
</body>
</html>
