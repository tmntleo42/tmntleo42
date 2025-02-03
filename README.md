<!DOCTYPE html>
<html>
<head>
    <title>Green Space</title>
    <style>
        body { text-align: center; font-family: Arial, sans-serif; background-color: black; color: white; overflow: hidden; }
        canvas { display: block; background-color: darkgreen; margin: auto; }
    </style>
</head>
<body>
    <h1>Green Space - Escape the Planet</h1>
    <canvas id="gameCanvas"></canvas>
    <script>
        const canvas = document.getElementById("gameCanvas");
        const ctx = canvas.getContext("2d");
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        let player = { x: 100, y: 100, width: 40, height: 40, speed: 5 };
        let bullets = [];

        function drawPlayer() {
            ctx.fillStyle = "blue";
            ctx.fillRect(player.x, player.y, player.width, player.height);
        }

        function shoot() {
            bullets.push({ x: player.x + player.width, y: player.y + player.height / 2, width: 10, height: 5, speed: 7 });
        }

        function drawBullets() {
            ctx.fillStyle = "red";
            bullets.forEach(bullet => {
                ctx.fillRect(bullet.x, bullet.y, bullet.width, bullet.height);
                bullet.x += bullet.speed;
            });
        }

        function updateGame() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            drawPlayer();
            drawBullets();
            requestAnimationFrame(updateGame);
        }

        document.addEventListener("keydown", (event) => {
            if (event.key === "ArrowUp") player.y -= player.speed;
            if (event.key === "ArrowDown") player.y += player.speed;
            if (event.key === "ArrowLeft") player.x -= player.speed;
            if (event.key === "ArrowRight") player.x += player.speed;
            if (event.key === " ") shoot();
        });

        updateGame();
    </script>
</body>
</html>





