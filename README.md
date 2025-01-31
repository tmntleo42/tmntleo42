<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Space-Themed Website</title>
    <style>
        body {
            margin: 0;
            height: 100vh;
            background: url('https://source.unsplash.com/1600x900/?space') no-repeat center center fixed;
            background-size: cover;
            animation: spaceBackground 30s infinite linear;
        }

        @keyframes spaceBackground {
            0% { background-position: 0 0; }
            100% { background-position: 100% 100%; }
        }

        /* Game container */
        .games-container {
            display: flex;
            justify-content: space-evenly;
            margin-top: 50px;
        }

        .game {
            border: 2px solid white;
            padding: 10px;
            background-color: rgba(0, 0, 0, 0.5);
            border-radius: 10px;
            width: 30%;
            text-align: center;
        }

        iframe {
            width: 100%;
            height: 300px;
            border-radius: 10px;
        }

        /* Proxy iframe container */
        .proxy-container {
            margin-top: 50px;
            text-align: center;
        }

        .proxy-container iframe {
            width: 100%;
            height: 500px;
            border-radius: 10px;
        }
    </style>
</head>
<body>
    <div class="games-container">
        <!-- WorldGuessr -->
        <div class="game">
            <h3>WorldGuessr</h3>
            <iframe src="https://worldguessr.com" frameborder="0"></iframe>
        </div>

        <!-- Any Car Game -->
        <div class="game">
            <h3>Car Game</h3>
            <iframe src="https://example.com/car-game" frameborder="0"></iframe>
        </div>

        <!-- Eaglercraft -->
        <div class="game">
            <h3>Eaglercraft</h3>
            <iframe src="https://eaglercraft.org" frameborder="0"></iframe>
        </div>
    </div>

    <!-- Proxy Browser -->
    <div class="proxy-container">
        <h3>Proxy Browser</h3>
        <iframe src="https://www.proxysite.com" frameborder="0"></iframe>
    </div>
</body>
</html>

