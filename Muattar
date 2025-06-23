<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Happy Birthday Muattar!</title>
  <style>
    body {
      text-align: center;
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to top right, #ffe5ec, #ffffff);
      margin: 0;
      padding: 0;
    }
    h1 {
      font-size: 2.5rem;
      color: #d6336c;
      margin-top: 30px;
    }
    .cake {
      margin-top: 50px;
    }
    canvas {
      border-radius: 10px;
    }
  </style>
</head>
<body>
  <h1>🎈 Happy Birthday to You, Muattar! 🎈</h1>
  <h2>Age: 20</h2>  <div class="cake">
    <canvas id="cakeCanvas" width="300" height="300"></canvas>
  </div>  <audio id="music" autoplay loop>
    <source src="https://cdn.pixabay.com/audio/2023/04/01/audio_62d6fa41b6.mp3" type="audio/mp3">
    Your browser does not support the audio element.
  </audio>  <script>
    const canvas = document.getElementById('cakeCanvas');
    const ctx = canvas.getContext('2d');
    let flameOn = true;

    function drawCake() {
      // Cake base
      ctx.fillStyle = '#f8c291';
      ctx.fillRect(100, 200, 100, 60);
      // Candle
      ctx.fillStyle = '#6c5ce7';
      ctx.fillRect(145, 160, 10, 40);
      // Flame
      if (flameOn) {
        ctx.beginPath();
        ctx.arc(150, 150, 10, 0, Math.PI * 2);
        ctx.fillStyle = '#fdcb6e';
        ctx.fill();
      }
    }

    function detectBlow() {
      navigator.mediaDevices.getUserMedia({ audio: true })
        .then(stream => {
          const audioContext = new (window.AudioContext || window.webkitAudioContext)();
          const mic = audioContext.createMediaStreamSource(stream);
          const analyser = audioContext.createAnalyser();
          mic.connect(analyser);
          analyser.fftSize = 512;
          const data = new Uint8Array(analyser.frequencyBinCount);

          function checkVolume() {
            analyser.getByteFrequencyData(data);
            let sum = 0;
            for (let i = 0; i < data.length; i++) {
              sum += data[i];
            }
            const volume = sum / data.length;
            if (volume > 40 && flameOn) {
              flameOn = false;
              drawCake();
              alert('You blew out the candle! 🚀');
            }
            requestAnimationFrame(checkVolume);
          }

          checkVolume();
        })
        .catch(err => {
          console.error('Mic access denied:', err);
        });
    }

    drawCake();
    detectBlow();
  </script></body>
</html>
