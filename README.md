<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>MLovely - Battle Jack Destiny</title>
    <style>
        /* Base Styling */
        body, html { margin: 0; padding: 0; overflow: hidden; background: #0a0a0a; height: 100%; width: 100%; font-family: 'Arial', sans-serif; }
        
        /* UI Header - Harinagar Metro */
        #header {
            position: absolute;
            top: 10px;
            width: 100%;
            text-align: center;
            z-index: 30;
        }
        .station-name { color: yellow; font-size: 18px; font-weight: bold; margin: 0; }
        .welcome-text { color: #00ff00; font-size: 14px; margin: 5px 0; }

        /* Game Title - BATTLE JACK DESTINY */
        #game-title {
            position: absolute;
            top: 60px;
            width: 100%;
            text-align: center;
            font-size: 22px;
            font-weight: 900;
            z-index: 25;
            letter-spacing: 2px;
        }
        .bj { color: white; }
        .destiny { color: #ff0000; text-shadow: 0 0 10px red; }

        /* GARENA STYLE INTERTWINED LOGO */
        #logo-wrapper {
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            display: flex;
            flex-direction: column;
            align-items: center;
            z-index: 20;
        }

        /* The Shield & Wings */
        #shield-container {
            position: relative;
            width: 140px;
            height: 140px;
            display: flex;
            justify-content: center;
            align-items: center;
        }

        /* The "M" and "L" merged */
        .intertwined-text {
            position: relative;
            font-size: 80px;
            font-weight: 900;
            line-height: 1;
            z-index: 10;
            filter: drop-shadow(0 0 15px rgba(255,255,255,0.5));
        }
        .m-char { color: #ffffff; position: relative; }
        .l-char { 
            color: #ffd700; 
            position: absolute; 
            left: 20px; 
            top: 10px; 
            opacity: 0.8; 
            font-size: 70px;
        }

        #mlovely-footer {
            margin-top: 10px;
            color: white;
            font-size: 24px;
            font-weight: bold;
            letter-spacing: 4px;
            text-shadow: 2px 2px 4px black;
        }

        /* Player Character */
        #player {
            position: absolute;
            width: 40px;
            height: 40px;
            background: #00ffff;
            border: 2px solid white;
            box-shadow: 0 0 20px #00ffff;
            left: 50%;
            top: 80%;
            border-radius: 5px;
            z-index: 5;
        }

        /* Joystick Control */
        #joystick-area {
            position: absolute;
            bottom: 50px;
            left: 50px;
            width: 120px;
            height: 120px;
            background: rgba(255,255,255,0.1);
            border: 2px solid rgba(255,255,255,0.3);
            border-radius: 50%;
            z-index: 100;
        }
        #stick {
            position: absolute;
            top: 35px;
            left: 35px;
            width: 50px;
            height: 50px;
            background: radial-gradient(circle, #ff0000, #8b0000);
            border-radius: 50%;
            box-shadow: 0 0 10px rgba(0,0,0,0.5);
        }
    </style>
</head>
<body>

    <div id="header">
        <p class="station-name">HARINAGAR METRO STATION</p>
        <p class="welcome-text">SWAAGAT BA PATNA METRO MEIN!</p>
    </div>

    <div id="game-title">
        <span class="bj">BATTLE JACK</span> <span class="destiny">DESTINY</span>
    </div>

    <div id="logo-wrapper">
        <div id="shield-container">
            <div class="intertwined-text">
                <span class="m-char">M</span>
                <span class="l-char">L</span>
            </div>
        </div>
        <div id="mlovely-footer">MLOVELY</div>
    </div>

    <div id="player"></div>

    <div id="joystick-area">
        <div id="stick"></div>
    </div>

</body>
</html>













