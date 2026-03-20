<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>MLovely Game</title>
    <style>
        body, html { margin: 0; padding: 0; overflow: hidden; background-color: #000; height: 100%; width: 100%; touch-action: none; font-family: sans-serif; }
        #ui { position: absolute; top: 10px; width: 100%; text-align: center; color: yellow; pointer-events: none; z-index: 10; }
        #player { position: absolute; width: 35px; height: 35px; background: #00ffff; border-radius: 5px; box-shadow: 0 0 15px #00ffff; left: 50%; top: 50%; }
        #joystick-base { position: absolute; bottom: 40px; left: 40px; width: 90px; height: 90px; background: rgba(255,255,255,0.1); border: 2px solid #fff; border-radius: 50%; }
        #stick { position: absolute; top: 20px; left: 20px; width: 50px; height: 50px; background: red; border-radius: 50%; }
    </style>
</head>
<body>
    <div id="ui">
        <h2 style="margin:0;">PATNA METRO - MLOVELY</h2>
        <p style="color: lime; margin:5px;">STATION: HARINAGAR | STATUS: ONLINE</p>
    </div>
    <div id="player"></div>
    <div id="joystick-base"><div id="stick"></div></div>

    <script>
        const player = document.getElementById('player');
        const stick = document.getElementById('stick');
        let px = window.innerWidth / 2;
        let py = window.innerHeight / 2;
        let moveX = 0, moveY = 0;

        window.addEventListener('touchmove', (e) => {
            let touch = e.touches[0];
            let base = document.getElementById('joystick-base').getBoundingClientRect();
            let dx = touch.clientX - (base.left + 45);
            let dy = touch.clientY - (base.top + 45);
            let dist = Math.min(Math.sqrt(dx*dx + dy*dy), 40);
            let angle = Math.atan2(dy, dx);
            
            stick.style.transform = `translate(${Math.cos(angle)*dist}px, ${Math.sin(angle)*dist}px)`;
            moveX = Math.cos(angle) * (dist / 10);
            moveY = Math.sin(angle) * (dist / 10);
        });

        window.addEventListener('touchend', () => {
            stick.style.transform = `translate(0px, 0px)`;
            moveX = 0; moveY = 0;
        });

        function gameLoop() {
            px += moveX;
            py += moveY;
            player.style.left = px + 'px';
            player.style.top = py + 'px';
            requestAnimationFrame(gameLoop);
        }
        gameLoop();
    </script>
</body>
</html>









