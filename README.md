<!DOCTYPE html>
<html lang="mn">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Khulan - Цагийн Тоолуур</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f7f7f7;
      margin: 0;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      height: 100vh;
    }
    h1 {
      font-size: 3em;
      margin-bottom: 20px;
    }
    .countdown {
      font-size: 1.5em;
      background: #fff;
      padding: 20px 30px;
      border-radius: 10px;
      box-shadow: 0 0 15px rgba(0, 0, 0, 0.1);
    }
  </style>
</head>
<body>
  <h1>Khulan</h1>
  <div class="countdown" id="countdown"></div>

  <script>
    // Тохируулах хугацаа: 2025 оны 2-р сарын 15
    const targetDate = new Date("2025-02-15T00:00:00").getTime();

    function updateCountdown() {
      const now = new Date().getTime();
      const distance = targetDate - now;

      // Өдөр, цаг, минут, секунд тооцоолох
      const days = Math.floor(distance / (1000 * 60 * 60 * 24));
      const hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      const minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
      const seconds = Math.floor((distance % (1000 * 60)) / 1000);

      // Тоолуулгыг харуулах
      document.getElementById("countdown").innerHTML =
        days + " өдөр, " + hours + " цаг, " + minutes + " минут, " + seconds + " секунд";

      // Хэрэв хугацаа дууссан бол
      if (distance < 0) {
        clearInterval(interval);
        document.getElementById("countdown").innerHTML = "Хугацаа дууссан!";
      }
    }

    // 1 секунд тутам шинэчлэх
    const interval = setInterval(updateCountdown, 1000);
    updateCountdown();
  </script>
</body>
</html>