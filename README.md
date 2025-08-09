<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>就吃我做的版本吧~</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #fff7f7;
            font-family: "Microsoft YaHei", sans-serif;
            font-size: 2.5rem;
            color: #ff6b81;
            animation: fadeIn 2s ease-in-out forwards;
            flex-direction: column;
            gap: 20px;
            overflow: hidden;
        }
        @keyframes fadeIn {
            0% { opacity: 0; transform: translateY(20px); }
            100% { opacity: 1; transform: translateY(0); }
        }
        .text {
            font-weight: bold;
            animation: float 3s ease-in-out infinite;
            z-index: 2;
        }
        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-10px); }
        }
        .heart {
            width: 50px;
            height: 50px;
            position: relative;
            animation: pulse 1.2s infinite;
            z-index: 2;
        }
        .heart::before,
        .heart::after {
            content: "";
            position: absolute;
            width: 50px;
            height: 80px;
            background: #ff6b81;
            border-radius: 50px 50px 0 0;
            top: 0;
        }
        .heart::before {
            left: 50px;
            transform: rotate(-45deg);
            transform-origin: 0 100%;
        }
        .heart::after {
            left: 0;
            transform: rotate(45deg);
            transform-origin: 100% 100%;
        }
        @keyframes pulse {
            0% { transform: scale(1); }
            50% { transform: scale(1.2); }
            100% { transform: scale(1); }
        }
        .falling-heart {
            position: fixed;
            top: -20px;
            color: #ff6b81;
            font-size: 20px;
            opacity: 0.8;
            animation: fall linear forwards;
        }
        @keyframes fall {
            to { transform: translateY(110vh) rotate(360deg); }
        }
    </style>
</head>
<body>
    <div class="text">就吃我做的版本吧~</div>
    <div class="heart"></div>

    <!-- 背景音乐 -->
    <audio id="bgMusic" autoplay loop>
        <source src="https://www.bensound.com/bensound-music/bensound-romantic.mp3" type="audio/mpeg">
    </audio>

    <script>
        // 爱心雨
        function createHeart() {
            const heart = document.createElement("div");
            heart.classList.add("falling-heart");
            heart.innerHTML = "❤";
            heart.style.left = Math.random() * 100 + "vw";
            heart.style.fontSize = Math.random() * 20 + 10 + "px";
            heart.style.animationDuration = (Math.random() * 3 + 3) + "s";
            document.body.appendChild(heart);

            setTimeout(() => {
                heart.remove();
            }, 6000);
        }
        setInterval(createHeart, 200);

        // 自动播放音乐（有些浏览器需要用户交互）
        document.body.addEventListener("click", () => {
            document.getElementById("bgMusic").play();
        });
    </script>
</body>
</html>
