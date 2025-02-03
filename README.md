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
        let enemies = [];
        let level = 1;
        let kills = 0;

        function drawPlayer() {
            ctx.fillStyle = "blue";
            ctx.fillRect(player.x, player.y, player.width, player.height);
        }

        function shoot() {
            bullets.push({ x: player.x + player.width, y: player.y + player.height / 2, width: 10, height: 5, speed: 7 });
        }

        function drawBullets() {
            ctx.fillStyle = "red";
            bullets.forEach((bullet, index) => {
                ctx.fillRect(bullet.x, bullet.y, bullet.width, bullet.height);
                bullet.x += bullet.speed;
                if (bullet.x > canvas.width) bullets.splice(index, 1);
            });
        }

        function spawnEnemy() {
            enemies.push({ x: canvas.width, y: Math.random() * canvas.height, width: 40, height: 40, speed: 1 + level * 0.5 });
        }

        function drawEnemies() {
            ctx.fillStyle = "green";
            enemies.forEach((enemy, index) => {
                ctx.fillRect(enemy.x, enemy.y, enemy.width, enemy.height);
                enemy.x -= enemy.speed;
                if (enemy.x + enemy.width < 0) enemies.splice(index, 1);
            });
        }

        function checkCollisions() {
            bullets.forEach((bullet, bIndex) => {
                enemies.forEach((enemy, eIndex) => {
                    if (
                        bullet.x < enemy.x + enemy.width &&
                        bullet.x + bullet.width > enemy.x &&
                        bullet.y < enemy.y + enemy.height &&
                        bullet.y + bullet.height > enemy.y
                    ) {
                        bullets.splice(bIndex, 1);
                        enemies.splice(eIndex, 1);
                        kills++;
                        if (kills >= 7) {
                            nextLevel();
                        }
                    }
                });
            });
        }

        function nextLevel() {
            if (level < 25) {
                level++;
                kills = 0;
                enemies = [];
                clearInterval(spawnInterval);
                spawnInterval = setInterval(spawnEnemy, Math.max(500, 2000 - level * 50));
            } else {
                endGame();
            }
        }

        function endGame() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = "white";
            ctx.font = "40px Arial";
            ctx.fillText("You escaped the planet!", canvas.width / 2 - 200, canvas.height / 2);
            ctx.fillText("Flying to Earth...", canvas.width / 2 - 150, canvas.height / 2 + 50);
        }

        function updateGame() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            ctx.fillStyle = "white";
            ctx.font = "20px Arial";
            ctx.fillText("Level: " + level, 20, 30);
            drawPlayer();
            drawBullets();
            drawEnemies();
            checkCollisions();
            requestAnimationFrame(updateGame);
        }

        document.addEventListener("keydown", (event) => {
            if (event.key === "ArrowUp") player.y -= player.speed;
            if (event.key === "ArrowDown") player.y += player.speed;
            if (event.key === "ArrowLeft") player.x -= player.speed;
            if (event.key === "ArrowRight") player.x += player.speed;
            if (event.key === " ") shoot();
        });

        let spawnInterval = setInterval(spawnEnemy, 2000);
        updateGame();
    </script>
</body>
</html>






