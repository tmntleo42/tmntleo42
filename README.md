## Hi there 👋
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Unblocked Games Hub</title>
    <style>
        body { font-family: Arial, sans-serif; text-align: center; background-color: #222; color: white; }
        h1 { color: #ffcc00; }
        .games-list { display: flex; flex-wrap: wrap; justify-content: center; }
        .game { margin: 10px; padding: 15px; background: #333; border-radius: 10px; }
        iframe { width: 80%; height: 500px; border: none; background: white; }
    </style>
</head>
<body>
    <h1>Unblocked Games Hub</h1>
    <div class="games-list">
        <div class="game"><a href="https://g.eags.us/eaglercraft/" target="_blank">Eaglercraft</a></div>
        <div class="game"><a href="https://worldgussr.github.io/" target="_blank">WorldGussr</a></div>
        <div class="game"><a href="https://s3.amazonaws.com/assets.crazygames.com/" target="_blank">Car Games</a></div>
        <div class="game"><a href="https://unblockedgames66ez.com/shooters" target="_blank">Shooter Games</a></div>
    </div>
    
    <h2>Proxy Browser</h2>
    <input type="text" id="proxyUrl" placeholder="Enter URL to unblock..." style="width: 60%; padding: 8px;">
    <button onclick="loadProxy()">Go</button>
    <br><br>
    <iframe id="proxyFrame"></iframe>
    
    <script>
        function loadProxy() {
            let url = document.getElementById('proxyUrl').value;
            if (url) {
                document.getElementById('proxyFrame').src = url;
            }
        }
    </script>
</body>
</html>
