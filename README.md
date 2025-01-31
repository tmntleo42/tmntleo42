<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Green Space-Themed Website</title>
    <style>
        /* General Reset */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: Arial, sans-serif;
            color: #fff;
            background: url('https://source.unsplash.com/1600x900/?space') no-repeat center center fixed;
            background-size: cover;
            height: 100vh;
            animation: spaceBackground 30s infinite linear;
        }

        /* Green Overlay */
        .overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background-color: rgba(0, 128, 0, 0.5); /* Green tint */
        }

        @keyframes spaceBackground {
            0% { background-position: 0 0; }
            100% { background-position: 100% 100%; }
        }

        /* Main container */
        .container {
            position: relative;
            z-index: 1;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
        }

        .title {
            font-size: 3rem;
            color: #66ff66; /* Bright Green */
            text-align: center;
            margin-bottom: 50px;
        }

        .games-container {
            display: flex;
            justify-content: space-evenly;
            gap: 20px;
            flex-wrap: wrap;
            width: 80%;
        }

        .game {
            width: 30%;
            text-align: center;
            background-color: rgba(0, 0, 0, 0.7); /* Dark background for the game containers */
            padding: 20px;
            border-radius: 15px;
            border: 2px solid #66ff66; /* Bright green border */
            transition: transform 0.3s ease;
        }

        .game:hover {
            transform: scale(1.05); /* Hover effect to enlarge */
        }

        iframe {
            width: 100%;
            height: 300px;
            border-radius: 10px;
            border: none;
        }

        /* Footer section */
        .footer {
            position: absolute;
            bottom: 20px;
            color: #66ff66;
            font-size: 1.2rem;
            text-align: center;
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .games-container {
                flex-direction: column;
                align-items: center;
            }
            .game {
                width: 80%;
                margin-bottom: 20px;
            }
        }
    </style>
</head>
<body>
    <div class="overlay"></div>

    <div class="container">
        <h1 class="title">Green Space-Themed Games</h1>

        <div class="games-container">
            <!-- WorldGuessr Game -->
            <div class="game">
                <h3>WorldGuessr</h3>
                <iframe src="https://your-proxy-url.com/proxy/worldguessr" frameborder="0"></iframe>
            </div>

            <!-- Car Game -->
            <div class="game">
                <h3>Car Game</h3>
                <iframe src="https://your-proxy-url.com/proxy/car-game" frameborder="0"></iframe>
            </div>

            <!-- Eaglercraft Game -->
            <div class="game">
                <h3>Eaglercraft</h3>
                <iframe src="https://your-proxy-url.com/proxy/eaglercraft" frameborder="0"></iframe>
            </div>
        </div>

        <!-- Footer -->
        <div class="footer">
            <p>&copy; 2025 Green Space Games | All rights reserved.</p>
        </div>
    </div>
</body>
</html>

        


