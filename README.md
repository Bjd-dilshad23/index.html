<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>MLovely Game</title>
    <style>
        body, html { margin: 0; padding: 0; overflow: hidden; background-color: #000; height: 100%; width: 100%; touch-action: none; }
        #joystick { position: absolute; bottom: 50px; left: 50px; width: 80px; height: 80px; background: rgba(255,255,255,0.2); border-radius: 50%; border: 2px solid #fff; }
        #stick { position: absolute; top: 20px; left: 20px; width: 40px; height: 40px; background: red; border-radius: 50%; }
        #player { position: absolute; width: 30px; height: 30px; background: cyan; top: 50%; left: 50%; border-radius: 5px; }
        #ui { position: absolute; top: 20px; width: 100%; text-align: center; color: yellow; font-family: sans-serif; }
    </style>
</head>
<body>
    <div id="ui"><h2>PATNA METRO - MLOVELY</h2><p>STATION: HARINAGAR</p></div>
    <div id="player"></div>
    <div id="joystick"><div id="stick"></div></div>
</body>
</html>







