<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>MLovely - Patna Metro</title>
    <style>
        body, html { margin: 0; padding: 0; overflow: hidden; background-color: #000; height: 100%; width: 100%; touch-action: none; font-family: 'Arial', sans-serif; }
        #ui { position: absolute; top: 15px; width: 100%; text-align: center; color: #ffff00; pointer-events: none; z-index: 10; text-shadow: 2px 2px #000; }
        #player { position: absolute; width: 35px; height: 35px; background: #00ffff; border-radius: 6px; box-shadow: 0 0 15px #00ffff; z-index: 5; left: 50%; top: 50%; }
        #joystick-base { position: absolute; bottom: 40px; left: 40px; width: 90px; height: 90px; background: rgba(255,255,255,0.1); border: 2px solid #fff; border-radius: 50%; touch-action: none; }
        #stick { position: absolute; top: 20px; left: 20px; width: 50px; height: 50px; background: #ff0000; border-radius: 50%; box-shadow: 0 0 10px #ff0000; pointer-events: none; }
    </style>
</head>
<body>
    <div id="ui">
        <h2 style="margin:0; font-size: 24px;">PATNA METRO - MLOVELY</h2>
        <p style="color: #00ff00; margin:5px; font-weight: bold;">STATION: HARINAGAR | SERVER: ONLINE</p>
    </div>

    <div id="player"></div>

    <div id="joystick-base">
        <div id="stick"></div>
    </div>

    <script>
        const player = document.getElementById('player');
        const stick = document.getElementById('stick');
        const base = document.getElementById('joystick-base');

        let px = window.innerWidth / 2;
        let py = window.innerHeight / 2;
        let moveX = 0, moveY = 0;
        let isTouching = false;

        const handleMove = (e) => {
            if (!isTouching) return;
            const touch = e.touches[0];
            const rect = base.getBoundingClientRect();
            const centerX = rect.left + rect.width / 2;
            const centerY = rect.top + rect.height / 2;
            
            let dx = touch.clientX - centerX;
            let dy = touch.clientY - centerY;
            const distance = Math.min(Math.sqrt(dx * dx + dy * dy), 35);
            const angle = Math.atan2(dy, dx);

            const tx = Math.cos(angle) * distance;
            const ty = Math.sin(angle) * distance;

            stick.style.transform = `translate(${tx}px, ${ty}px)`;
            
            // Movement speed control
            moveX = (tx / 35) * 6;
            moveY = (ty / 35) * 6;
        };

        base.addEventListener('touchstart', (e) => { isTouching = true; handleMove(e); });
        window.addEventListener('touchmove', (e) => { handleMove(e); }, { passive: false });
        window.addEventListener('touchend', () => {
            isTouching = false;
            moveX = 0; moveY = 0;
            stick.style.transform = `translate(0px, 0px)`;
        });

        function gameLoop() {
            px += moveX;
            py += moveY;

            // Screen boundaries to keep player inside
            px = Math.max(0, Math.min(window.innerWidth - 35, px));
            py = Math.max(0, Math.min(window.innerHeight - 35, py));

            player.style.left = px + 'px';
            player.style.top = py + 'px';
            requestAnimationFrame(gameLoop);
        }
        gameLoop();
    </script>
</body>
</html>










