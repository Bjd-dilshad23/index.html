<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>MLovely - BJD Game</title>
    <style>
        body, html { margin: 0; padding: 0; overflow: hidden; background-color: #111; height: 100%; width: 100%; touch-action: none; font-family: sans-serif; }
        canvas { display: block; }
        #joystick-base { position: absolute; bottom: 40px; left: 40px; width: 100px; height: 100px; background: rgba(255,255,255,0.2); border-radius: 50%; }
        #joystick-stick { position: absolute; top: 25px; left: 25px; width: 50px; height: 50px; background: red; border-radius: 50%; }
        #ui { position: absolute; top: 10px; width: 100%; text-align: center; color: yellow; pointer-events: none; }
    </style>
</head>
<body>
    <div id="ui"><h3>PATNA METRO - MLOVELY STATION</h3></div>
    <canvas id="gameCanvas"></canvas>
    <div id="joystick-base"><div id="joystick-stick"></div></div>
    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.getContext('2d');
        const stick = document.getElementById('joystick-stick');
        canvas.width = window.innerWidth; canvas.height = window.innerHeight;
        let player = { x: canvas.width/2, y: canvas.height/2, size: 25 };
        let moveX = 0, moveY = 0;
        window.addEventListener('touchmove', (e) => {
            let touch = e.touches[0];
            let base = document.getElementById('joystick-base').getBoundingClientRect();
            let dx = touch.clientX - (base.left + 50);
            let dy = touch.clientY - (base.top + 50);
            let dist = Math.sqrt(dx*dx + dy*dy);
            if (dist < 50) {
                stick.style.transform = `translate(${dx}px, ${dy}px)`;
                moveX = dx/10; moveY = dy/10;
            }
        });
        window.addEventListener('touchend', () => {
            stick.style.transform = `translate(0px, 0px)`;
            moveX = 0; moveY = 0;
        });
        function draw() {
            ctx.fillStyle = '#222'; ctx.fillRect(0,0,canvas.width,canvas.height);
            ctx.strokeStyle = 'yellow'; ctx.strokeRect(20,20,canvas.width-40,canvas.height-40);
            player.x += moveX; player.y += moveY;
            ctx.fillStyle = '#00ffff'; ctx.fillRect(player.x, player.y, player.size, player.size);
            requestAnimationFrame(draw);
        }
        draw();
    </script>
</body>
</html>




