<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>PrintPay</title>
  <style>
    body {
      margin: 0;
      background-color: #f4f4f4;
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      flex-direction: column;
    }

    #fingerprint {
      width: 150px;
      height: 150px;
      background-image: url('https://upload.wikimedia.org/wikipedia/commons/thumb/e/e3/Fingerprint_icon.svg/1200px-Fingerprint_icon.svg.png');
      background-size: cover;
      background-position: center;
      cursor: pointer;
      opacity: 0.7;
      transition: opacity 0.3s;
    }

    #fingerprint:active {
      opacity: 1;
    }

    #message {
      margin-top: 30px;
      font-size: 20px;
      color: #333;
      text-align: center;
      display: none;
    }
  </style>
</head>
<body>
  <div id="fingerprint"></div>
  <div id="message">Thank you for paying with PrintPay</div>

  <script>
    const fingerprint = document.getElementById('fingerprint');
    const message = document.getElementById('message');
    let pressTimer;

    fingerprint.addEventListener('touchstart', () => {
      pressTimer = setTimeout(() => {
        message.style.display = 'block';
      }, 3000); // 3 seconds
    });

    fingerprint.addEventListener('touchend', () => {
      clearTimeout(pressTimer);
    });

    // Support for mouse click (optional for desktop)
    fingerprint.addEventListener('mousedown', () => {
      pressTimer = setTimeout(() => {
        message.style.display = 'block';
      }, 3000);
    });

    fingerprint.addEventListener('mouseup', () => {
      clearTimeout(pressTimer);
    });
  </script>
</body>
</html>
