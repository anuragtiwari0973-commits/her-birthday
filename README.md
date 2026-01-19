<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Happy Birthday Anushka!</title>
    <script src="https://cdn.jsdelivr.net/npm/canvas-confetti@1.6.0/dist/confetti.browser.min.js"></script>
    <style>
        :root {
            --primary-pink: #ff758c;
            --secondary-pink: #ff7eb3;
        }

        body {
            margin: 0;
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            background: linear-gradient(135deg, #fa709a 0%, #fee140 100%);
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            overflow: hidden;
        }

        .container {
            text-align: center;
            z-index: 10;
        }

        #surpriseBtn {
            padding: 20px 40px;
            font-size: 1.5rem;
            background: white;
            color: #ff758c;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            box-shadow: 0 10px 20px rgba(0,0,0,0.2);
            transition: all 0.3s ease;
            font-weight: bold;
            animation: pulse 2s infinite;
        }

        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.05); }
            100% { transform: scale(1); }
        }

        #birthdayContent {
            display: none;
            background: rgba(255, 255, 255, 0.9);
            padding: 40px;
            border-radius: 30px;
            box-shadow: 0 20px 50px rgba(0,0,0,0.2);
            max-width: 400px;
            animation: popIn 0.8s cubic-bezier(0.175, 0.885, 0.32, 1.275);
        }

        @keyframes popIn {
            0% { transform: scale(0); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        h1 {
            color: #ff4757;
            margin: 0;
            font-size: 2.5rem;
        }

        .name-glow {
            display: block;
            font-size: 3.5rem;
            color: #ff7eb3;
            text-shadow: 0 0 10px rgba(255,126,179,0.5);
            margin: 10px 0;
        }

        p {
            color: #444;
            line-height: 1.6;
            font-size: 1.1rem;
        }

        /* Floating Hearts Background */
        .heart {
            position: absolute;
            color: rgba(255, 255, 255, 0.5);
            font-size: 20px;
            user-select: none;
            pointer-events: none;
            animation: float 5s linear infinite;
        }

        @keyframes float {
            0% { transform: translateY(100vh) rotate(0deg); opacity: 1; }
            100% { transform: translateY(-10vh) rotate(360deg); opacity: 0; }
        }
    </style>
</head>
<body>

    <div class="container">
        <button id="surpriseBtn">Anushka, Open Your Gift! 🎁</button>

        <div id="birthdayContent">
            <h1>Happy Birthday</h1>
            <span class="name-glow">Anushka!</span>
            <p>  "To the girl who turns every ordinary moment into a magical memory...",
            "May your year be as bright as your soul and as beautiful as your heart.",
            "Keep shining, keep smiling, and keep being the incredible human you are.",
            "The world is a better place just because you're in it. Happy Birthday, Anushka!"</p>
            <p style="font-size: 0.9rem;">✨ ✨ ✨</p>
        </div>
    </div>

    <script>
        const btn = document.getElementById('surpriseBtn');
        const content = document.getElementById('birthdayContent');

        // Create background floating hearts
        function createHeart() {
            const heart = document.createElement('div');
            heart.classList.add('heart');
            heart.innerHTML = '❤️';
            heart.style.left = Math.random() * 100 + 'vw';
            heart.style.animationDuration = (Math.random() * 3 + 2) + 's';
            document.body.appendChild(heart);
            setTimeout(() => heart.remove(), 5000);
        }
        setInterval(createHeart, 300);

        btn.addEventListener('click', () => {
            btn.style.display = 'none';
            content.style.display = 'block';

            // Custom Anushka Confetti (Pinks and Gold)
            const count = 200;
            const defaults = { origin: { y: 0.7 } };

            function fire(particleRatio, opts) {
                confetti(Object.assign({}, defaults, opts, {
                    particleCount: Math.floor(count * particleRatio),
                    colors: ['#ff758c', '#ff7eb3', '#fee140', '#ffffff']
                }));
            }

            fire(0.25, { spread: 26, startVelocity: 55 });
            fire(0.2, { spread: 60 });
            fire(0.35, { spread: 100, decay: 0.91, scalar: 0.8 });
            fire(0.1, { spread: 120, startVelocity: 25, decay: 0.92, scalar: 1.2 });
            fire(0.1, { spread: 120, startVelocity: 45 });
        });
    </script>
</body>
</html>
