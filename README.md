<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>MLovely - Patna Metro</title>
    <style>
        body, html { margin: 0; padding: 0; overflow: hidden; background: #0a0a0a; height: 100%; width: 100%; touch-action: none; font-family: 'Montserrat', sans-serif; }
        
        /* New Game Title Style */
        #game-title {
            position: absolute;
            top: 25px;
            width: 100%;
            text-align: center;
            font-size: 20px;
            font-weight: bold;
            text-transform: uppercase;
            color: #d8dcd1; /* Light gray text */
            z-index: 20;
            pointer-events: none;
        }
        #game-title .battle-jack { color: #d8dcd1; }
        #game-title .destiny { color: #c00000; /* Deep red for Destiny */ }

        /* Mlovely Intertwined Logo in Shield with Wings */
        #logo-container {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            display: flex;
            flex-direction: column;
            align-items: center;
            z-index: 20;
            pointer-events: none;
        }
        #shield {
            width: 100px;
            height: 120px;
            background: rgba(192, 0, 0, 0.2); /* Reddish-pink transparent shield */
            border: 4px solid #bda88a; /* Matte gold border */
            border-bottom: 8px solid #bda88a; /* Pointy bottom */
            border-radius: 5px;
            position: relative;
            box-shadow: 0 0 15px rgba(192,0,0,0.5);
            display: flex;
            justify-content: center;
            align-items: center;
        }
        #shield::after { /* Wing shape with white/red color */
            content: '';
            position: absolute;
            top: 20px;
            left: -35px;
            width: 170px;
            height: 70px;
            background: linear-gradient(to bottom, #d8dcd1 50%, #c00000 50%); /* Gradient of white and red */
            border-radius: 50% 50% 0 0 / 100% 100% 0 0;
            z-index: 10;
        }
        #mlovely-text {
            color: #d8dcd1;
            font-size: 26px;
            font-weight: bold;
            margin-top: -15px; /* Adjust spacing below shield */
            z-index: 20;
        }
        
        /* Standard UI and Character */
        #ui { position: absolute; top: 10px; width: 100%; text-align: center; color: yellow; z-index: 10; pointer-events: none; }
        #player { position: absolute; width: 35px; height: 35px; background: #00ffff; border: 2px solid white; border-radius: 6px; box-shadow: 0 0 15px #00ffff; z-index: 5; left: 50%; top: 50%; }
        #joystick-base { position: absolute; bottom: 40px; left: 40px; width: 100px; height: 100px; background: rgba(255,255,255,0.1); border: 2px solid #fff; border-radius: 50%; }
        #stick { position: absolute; top: 25px; left: 25px; width: 50px; height: 50px; background: radial-gradient(circle, red, darkred); border-radius: 50%; }
    </style>
</head>
<body>
    <div id="game-title">
        <span class="battle-jack">BATTLE JACK</span> <span class="destiny">DESTINY</span>
    </div>
    
    <div id="logo-container">
        <div id="shield">
            <div style="font-size: 60px; font-weight: bold; color: white; margin-bottom: 20px;">M</div>
            <div style="font-size: 40px; font-weight: bold; color: gold; margin-top: -30px;">L</div>
        </div>
        <div id="mlovely-text">MLOVELY</div>
    </div>
    
    <div id="ui">
        <h3 style="margin:0;">HARINAGAR METRO STATION</h3>
        <p style="color: lime; margin:5px;">SWAAGAT BA PATNA METRO MEIN!</p>
    </div>

    <div id="player"></div>
    <div id="joystick-base"><div id="stick"></div></div>

    <script>
        // Keep your original smooth movement script here
        // ... (The movement logic remains unchanged) ...
    </script>
</body>
</html>













