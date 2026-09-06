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

    /* Неоновая сетка на фоне */
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

    .info {
      margin-bottom: 30px;
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

    /* Кнопка */

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

    /* Блик при наведении */

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

    /* Сообщение после нажатия */

    #message {
      margin-top: 20px;

      color: #00d9ff;

      font-size: 17px;
      font-weight: bold;

      opacity: 0;
      transform: translateY(10px);

      transition: 0.4s ease;
    }

    #message.show {
      opacity: 1;
      transform: translateY(0);
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

    <button class="pay-button" onclick="paid()">
      Я оплатил
    </button>

    <div id="message">
      ✓ Спасибо! Информация отправлена.
    </div>

  </div>

  <script>
    function paid() {
      const message = document.getElementById("message");

      message.classList.add("show");
    }
  </script>

</body>
</html>
