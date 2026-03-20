<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>MLovely - Patna Metro</title>
    <style>
        body, html { margin: 0; padding: 0; overflow: hidden; background: #1a1a1a; height: 100%; width: 100%; touch-action: none; font-family: 'Arial', sans-serif; }
        
        /* ML Intertwined Logo */
        #logo { position: absolute; top: 10px; left: 10px; font-size: 24px; font-weight: bold; color: #ff4500; text-shadow: 2px 2px #000; z-index: 20; }
        #logo span { color: #fff; margin-left: -8px; }

        #ui { position: absolute; top: 15px; width: 100%; text-align: center; color: #ffff00; pointer-events: none; z-index: 10; }
        
        /* Character Box */
        #player { position: absolute; width: 35px; height: 35px; background: #00ffff; border: 2px solid #fff; border-radius: 4px; box-shadow: 0 0 15px #00ffff; z-index: 5; }

        #joystick-base { position: absolute; bottom: 40px; left: 40px; width: 90px; height: 90px; background: rgba(255,255,255,0.1); border: 2px solid rgba(255,255,255,0.5); border-radius: 50%; }
        #stick { position: absolute; top: 20px; left: 20px; width: 50px; height: 50px; background: radial-gradient(circle, #ff0000, #8b0000); border-radius: 50%; box-shadow: 0 0 10px #ff0000; }

        /* Background Grid (Metro Floor jaisa) */
        #grid { position: absolute; width: 2000px; height: 2000px; background-image: linear-gradient(#333 1px, transparent 1px), linear-gradient(90deg, #333 1px, transparent 1px); background-size: 50px 50px; z-index: 1; }
    </style>
</head>
<body>
    <div id="logo">M<span>L</span>ovely</div>
    
    <div id="ui">
        <h3 style="margin:0;">HARINAGAR METRO STATION</h3>
        <p style="color: #00ff00; margin:2px; font-size:12px;">BHOJPURI/HINDI MODE: ON</p>
    </div>

    <div id="grid"></div>
    <div id="player"></div>

    <div id="joystick-base">
        <div id="stick"></div>
    </div>

    <script>
        const player = document.getElementById('player');
        const stick = document.getElementById('stick');
        const base = document.getElementById('joystick-base');
        const grid = document.getElementById('grid');

        let px = window.innerWidth / 2;
        let py = window.innerHeight / 2;
        let gx = 0, gy = 0;
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

            stick.style.transform = `translate(${Math.cos(angle) * distance}px, ${Math.sin(angle) * distance}px)`;
            
            moveX = (Math.cos(angle) * distance / 35) * 5;
            moveY = (Math.sin(angle) * distance / 35) * 5;
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

            // Boundaries
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











