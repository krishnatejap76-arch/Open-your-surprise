<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>For My Bestie MoMo 🎀</title>
    <style>
        body {
            margin: 0;
            padding: 0;
            height: 100vh;
            background: #f0f4ff; /* Soft blue/purple for friendship */
            font-family: 'Comic Sans MS', 'Arial', sans-serif;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* Continuous Floating Background with Teddies & Balloons */
        .bg-container {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: 1;
            pointer-events: none;
        }

        .float-icon {
            position: absolute;
            bottom: -50px;
            opacity: 0.7;
            animation: moveUp 5s linear infinite;
        }

        @keyframes moveUp {
            to {
                transform: translateY(-110vh) rotate(360deg);
            }
        }

        /* Main Friendship Card */
        .card {
            background: rgba(255, 255, 255, 0.98);
            padding: 40px;
            border-radius: 30px;
            box-shadow: 0 20px 50px rgba(0, 123, 255, 0.2);
            text-align: center;
            border: 5px solid #74b9ff;
            z-index: 10;
            width: 350px;
            position: relative;
        }

        h1 {
            color: #0984e3;
            font-size: 1.8rem;
            margin-bottom: 20px;
            line-height: 1.4;
        }

        .sub-text {
            color: #636e72;
            margin-bottom: 30px;
            font-size: 1.1rem;
        }

        .buttons {
            display: flex;
            justify-content: space-around;
            align-items: center;
            height: 100px;
        }

        button {
            padding: 15px 30px;
            font-size: 1.1rem;
            font-weight: bold;
            border: none;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.2s ease;
        }

        #yesBtn {
            background: #74b9ff;
            color: white;
            box-shadow: 0 5px 15px rgba(116, 185, 255, 0.4);
        }

        /* The Escaping No Button */
        #noBtn {
            background: #dfe6e9;
            color: #636e72;
            position: fixed;
            z-index: 999;
        }

        #success {
            display: none;
        }

        .bestie-text {
            color: #d63384;
            font-size: 1.4rem;
            font-weight: bold;
            line-height: 1.6;
        }
    </style>
</head>
<body>

    <div class="bg-container" id="bg"></div>

    <div class="card" id="mainCard">
        <div id="ask">
            <h1>Hey MoMo! ✨</h1>
            <p class="sub-text">will you be my best friend <br>you are my <b>Best Friend</b> 🫂</p>
            <div class="buttons">
                <button id="yesBtn">Yes, Forever! 🤝</button>
                <button id="noBtn">No</button>
            </div>
        </div>

        <div id="success">
            <p class="bestie-text">best choice ever <br><br> BEST FRIENDS FOREVER! 🥰😘</p>
            <div style="font-size: 3.5rem; margin-top: 20px;">🧸✨🍭🎈</div>
            <p style="color: #0984e3; font-weight: bold;"></p>
        </div>
    </div>

    <script>
        const noBtn = document.getElementById('noBtn');
        const yesBtn = document.getElementById('yesBtn');
        const askDiv = document.getElementById('ask');
        const successDiv = document.getElementById('success');
        const bg = document.getElementById('bg');

        // --- 1. THE ESCAPING LOGIC ---
        const escape = () => {
            const padding = 60;
            const maxX = window.innerWidth - noBtn.offsetWidth - padding;
            const maxY = window.innerHeight - noBtn.offsetHeight - padding;
            
            const randomX = Math.floor(Math.random() * maxX);
            const randomY = Math.floor(Math.random() * maxY);
            
            noBtn.style.left = randomX + 'px';
            noBtn.style.top = randomY + 'px';
        };

        noBtn.addEventListener('mouseover', escape);
        noBtn.addEventListener('click', escape);
        noBtn.addEventListener('touchstart', (e) => {
            e.preventDefault();
            escape();
        });

        // --- 2. THE BACKGROUND DECORATION ---
        // Mixture of Teddies, Balloons, and Hearts
        const icons = ['🧸', '🎈', '✨', '💎', '🍭', '🧸', '🎈', '💙'];
        function addIcon() {
            const icon = document.createElement('div');
            icon.className = 'float-icon';
            icon.innerText = icons[Math.floor(Math.random() * icons.length)];
            icon.style.left = Math.random() * 100 + 'vw';
            icon.style.fontSize = (Math.random() * 20 + 25) + 'px';
            icon.style.animationDuration = (Math.random() * 2 + 4) + 's';
            bg.appendChild(icon);
            
            setTimeout(() => icon.remove(), 5000);
        }
        
        // Background starts immediately
        setInterval(addIcon, 400);

        // --- 3. THE YES CLICK ---
        yesBtn.addEventListener('click', () => {
            askDiv.style.display = 'none';
            noBtn.style.display = 'none';
            successDiv.style.display = 'block';
            
            // Celebration: Explode with icons!
            setInterval(addIcon, 80); 
            document.body.style.background = "#e3f2fd";
        });
    </script>
</body>
</html>

