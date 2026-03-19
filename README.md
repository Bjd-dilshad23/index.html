<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>MLovely - BJD Game</title>
    <style>
        body, html { margin: 0; padding: 0; overflow: hidden; background-color: #000; height: 100%; width: 100%; touch-action: none; font-family: sans-serif; }
        canvas { display: block; background: #1a1a1a; }
        #ui-layer { position: absolute; top: 10px; width: 100%; text-align: center; color: yellow; pointer-events: none; }
        #joystick-base { position: absolute; bottom: 40px; left: 40px; width: 100px; height: 100px; background: rgba(255,255,255,0.1); border: 2px solid rgba(255,255,255,0.3); border-radius: 50%; }
        #joystick-stick { position: absolute; top: 25px; left: 25px; width: 50px; height: 50px; background: red; border-radius: 50%; opacity: 0.7; }
    </style>
</head>
<body>
    <div id="ui-layer">
        <h2 id="status">MLOVELY - PATNA METRO STATION</h2>
    </div>
    <canvas id="gameCanvas"></canvas>
    <div id="joystick-base"><div id="joystick-stick"></div></div>

    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');
        const stick = document.getElementById('joystick-stick');
        
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;

        let player = { x: canvas.width/2, y: canvas.height/2, size: 25, color: '#00ffff' };
        let moveX = 0, moveY = 0;

        // Joystick Logic
        window.addEventListener('touchmove', (e) => {
            let touch = e.touches[0];
            let base = document.getElementById('joystick-base').getBoundingClientRect();
            let centerX = base.left + 50;
            let centerY = base.top + 50;
            
            let dx = touch.clientX - centerX;
            let dy = touch.clientY - centerY;
            let dist = Math.sqrt(dx*dx + dy*dy);
            
            if (dist < 60) {
                stick.style.transform = `translate(${dx}px, ${dy}px)`;
                moveX = dx / 15;
                moveY = dy / 15;
            }
        });

        window.addEventListener('touchend', () => {
            stick.style.transform = `translate(0px, 0px)`;
            moveX = 0; moveY = 0;
        });

        function gameLoop() {
            ctx.clearRect(0, 0, canvas.width, canvas.height);
            
            // Draw Metro Platform Lines
            ctx.strokeStyle = '#ffff00';
            ctx.lineWidth = 5;
            ctx.strokeRect(20, 20, canvas.width-40, canvas.height-40);

            // Move & Draw Player
            player.x += moveX;
            player.y += moveY;
            
            ctx.fillStyle = player.color;
            ctx.shadowBlur = 15;
            ctx.shadowColor = player.color;
            ctx.fillRect(player.x, player.y, player.size, player.size);
            
            requestAnimationFrame(gameLoop);
        }
        gameLoop();
    </script>
</body>
</html>



