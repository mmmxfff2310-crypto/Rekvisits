<!DOCTYPE html>
<html lang="ru">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Реквизиты</title>
  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    body {
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      font-family: Arial, sans-serif;
      color: white;
      background:
        radial-gradient(circle at 50% 0%, #006eff 0%, transparent 40%),
        linear-gradient(135deg, #020617, #001b52, #000817);
      overflow: hidden;
    }
    body::before {
      content: "";
      position: fixed;
      inset: 0;
      background-image:
        radial-gradient(#00bfff 1px, transparent 1px);
      background-size: 35px 35px;
      opacity: 0.12;
      pointer-events: none;
    }
    .container {
      width: 90%;
      max-width: 500px;
      padding: 45px 30px;
      text-align: center;
      background: rgba(0, 20, 65, 0.85);
      border: 1px solid rgba(0, 190, 255, 0.8);
      border-radius: 25px;
      box-shadow:
        0 0 20px rgba(0, 140, 255, 0.5),
        0 0 60px rgba(0, 100, 255, 0.25),
        inset 0 0 30px rgba(0, 140, 255, 0.08);
      backdrop-filter: blur(12px);
      position: relative;
      z-index: 1;
      animation: appear 0.8s ease;
    }
    @keyframes appear {
      from {
        opacity: 0;
        transform: translateY(30px) scale(0.95);
      }
      to {
        opacity: 1;
        transform: translateY(0) scale(1);
      }
    }
    h1 {
      font-size: clamp(42px, 10vw, 65px);
      margin-bottom: 35px;
      color: #ffffff;
      text-shadow:
        0 0 5px #00d9ff,
        0 0 15px #00aaff,
        0 0 30px #0077ff,
        0 0 60px #0055ff;
      animation: neon 2s ease-in-out infinite alternate;
    }
    @keyframes neon {
      from {
        text-shadow:
          0 0 5px #00d9ff,
          0 0 15px #00aaff,
          0 0 30px #0077ff;
      }
      to {
        text-shadow:
          0 0 10px white,
          0 0 25px #00d9ff,
          0 0 50px #0077ff,
          0 0 80px #0055ff;
      }
    }
    .block {
      padding: 18px;
      margin-bottom: 18px;
      border-radius: 15px;
      background: rgba(0, 80, 180, 0.18);
      border: 1px solid rgba(0, 180, 255, 0.35);
      transition: 0.3s ease;
    }
    .block:hover {
      transform: translateY(-3px);
      border-color: #00c8ff;
      box-shadow:
        0 0 15px rgba(0, 180, 255, 0.5);
    }
    .label {
      color: #7fcfff;
      font-size: 16px;
      margin-bottom: 8px;
    }
    .value {
      font-size: 24px;
      font-weight: bold;
      color: white;
      text-shadow:
        0 0 10px #008cff;
    }
    /* Кнопка оплаты */
    .pay-button {
      position: relative;
      width: 100%;
      margin-top: 15px;
      padding: 17px 25px;
      border: none;
      border-radius: 15px;
      color: white;
      font-size: 20px;
      font-weight: bold;
      cursor: pointer;
      background: linear-gradient(
        90deg,
        #005eff,
        #00bfff,
        #006eff
      );
      background-size: 200% 100%;
      box-shadow:
        0 0 15px rgba(0, 170, 255, 0.7);
      transition:
        transform 0.25s ease,
        box-shadow 0.25s ease,
        background-position 0.5s ease;
      overflow: hidden;
    }
    .pay-button:hover {
      transform: translateY(-4px) scale(1.02);
      background-position: 100% 0;
      box-shadow:
        0 0 20px #00c8ff,
        0 0 45px #006eff,
        0 0 70px rgba(0, 150, 255, 0.5);
    }
    .pay-button:active {
      transform: scale(0.96);
    }
    .pay-button::before {
      content: "";
      position: absolute;
      top: 0;
      left: -100%;
      width: 60%;
      height: 100%;
      background: linear-gradient(
        90deg,
        transparent,
        rgba(255,255,255,0.45),
        transparent
      );
      transform: skewX(-20deg);
      transition: left 0.6s ease;
    }
    .pay-button:hover::before {
      left: 140%;
    }
    /* Таймер */
    #timerBlock {
      display: none;
      margin-top: 25px;
      padding: 20px;
      border-radius: 15px;
      background: rgba(0, 90, 200, 0.18);
      border: 1px solid rgba(0, 190, 255, 0.4);
      animation: fadeIn 0.5s ease;
    }
    #timerText {
      font-size: 17px;
      color: #9edfff;
      margin-bottom: 10px;
    }
    #timer {
      font-size: 42px;
      font-weight: bold;
      color: #00d9ff;
      text-shadow:
        0 0 10px #00c8ff,
        0 0 25px #0077ff;
    }
    /* Финальное сообщение */
    #message {
      display: none;
      margin-top: 20px;
      padding: 20px;
      border-radius: 15px;
      background: rgba(0, 90, 200, 0.2);
      border: 1px solid rgba(0, 200, 255, 0.5);
      animation: fadeIn 0.6s ease;
    }
    #messageText {
      font-size: 17px;
      line-height: 1.5;
      color: #ffffff;
      margin-bottom: 15px;
    }
    .number {
      display: block;
      font-size: 22px;
      font-weight: bold;
      color: #00d9ff;
      margin-bottom: 15px;
      text-shadow:
        0 0 10px #008cff;
    }
    /* Кнопка копирования */
    .copy-button {
      width: 100%;
      padding: 13px 20px;
      border: 1px solid #00bfff;
      border-radius: 12px;
      background: rgba(0, 150, 255, 0.2);
      color: white;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
      transition: 0.3s ease;
    }
    .copy-button:hover {
      background: rgba(0, 180, 255, 0.35);
      box-shadow:
        0 0 15px rgba(0, 190, 255, 0.5);
    }
    /* Красное предупреждение */
    .warning {
      margin-top: 25px;
      color: #ff3333;
      font-size: 12px;
      line-height: 1.4;
      text-shadow:
        0 0 5px rgba(255, 0, 0, 0.35);
    }
    @keyframes fadeIn {
      from {
        opacity: 0;
        transform: translateY(10px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }
    @media (max-width: 500px) {
      .container {
        padding: 35px 20px;
      }
      .value {
        font-size: 20px;
      }
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Реквизиты</h1>
    <div class="block">
      <div class="label">Номер телефона</div>
      <div class="value">79996512682</div>
    </div>
    <div class="block">
      <div class="label">Название банка</div>
      <div class="value">Т-Банк</div>
    </div>
    <button class="pay-button" id="payButton" onclick="paid()">
      Я оплатил
    </button>
    <!-- Таймер -->
    <div id="timerBlock">
      <div id="timerText">
        Подождите, пожалуйста...
      </div>
      <div id="timer">
        10
      </div>
    </div>
    <!-- Сообщение после таймера -->
    <div id="message">
      <div id="messageText">
        Отправьте подтверждение об отправке платежа
        в любой мессенджер, например
        <b>WhatsApp</b> или <b>MAX</b>,
        на номер:
      </div>
      <span class="number" id="phoneNumber">
        799965126282
      </span>
      <button class="copy-button" onclick="copyNumber()">
        📋 Скопировать номер
      </button>
    </div>
    <!-- Предупреждение -->
    <div class="warning">
      Если я не отвечаю, я не СКАМЕР — просто занят
      и скоро отвечу.
    </div>
  </div>
  <script>
    let timerInterval;
    function paid() {
      const payButton = document.getElementById("payButton");
      const timerBlock = document.getElementById("timerBlock");
      const timer = document.getElementById("timer");
      const message = document.getElementById("message");
      // Скрываем кнопку
      payButton.style.display = "none";
      // Показываем таймер
      timerBlock.style.display = "block";
      // Сбрасываем таймер
      let seconds = 10;
      timer.textContent = seconds;
      clearInterval(timerInterval);
      timerInterval = setInterval(function() {
        seconds--;
        timer.textContent = seconds;
        if (seconds <= 0) {
          clearInterval(timerInterval);
          // Скрываем таймер
          timerBlock.style.display = "none";
          // Показываем сообщение
          message.style.display = "block";
        }
      }, 1000);
    }
    function copyNumber() {
      const number = document.getElementById("phoneNumber").textContent.trim();
      navigator.clipboard.writeText(number)
        .then(function() {
          const button = document.querySelector(".copy-button");
          button.textContent = "✓ Номер скопирован!";
          setTimeout(function() {
            button.textContent = "📋 Скопировать номер";
          }, 2000);
        })
        .catch(function() {
          alert("Не удалось скопировать номер. Скопируйте его вручную: " + number);
        });
    }
  </script>
</body>
</html>

Важно: я делаю возврат средств при
условии что я не смог его выполнить,
а так первые 2 покупки могу вернуть
