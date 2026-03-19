<!DOCTYPE html>
<html lang="hi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>MLovely - BJD Game</title>
    <style>
        body, html { margin: 0; padding: 0; overflow: hidden; background-color: #222; height: 100%; width: 100%; touch-action: none; }
        canvas { display: block; }
        #joystick-container { position: absolute; bottom: 50px; left: 50px; width: 100px; height: 100px; background: rgba(255,255,255,0.2); border-radius: 50%; display: flex; align-items: center; justify-content: center; }
        #joystick-knob { width: 50px; height: 50px; background: rgba(255,0,0,0.6); border-radius: 50%; position: relative; }
    </style>
</head>
<body>
    <canvas id="gameCanvas"></canvas>
    <div id="joystick-container"><div id="joystick-knob"></div></div>

    <script>
        const canvas = document.getElementById('gameCanvas');
        const ctx = canvas.width = window.innerWidth;
        const cHeight = canvas.height = window.innerHeight;
        const context = canvas.getContext('2d');

        let player = { x: 200, y: 200, size: 30, color: 'cyan' };
        let moveX = 0, moveY = 0;

        function drawMap() {
            // Patna Metro Platform Drawing
            context.fillStyle = '#555'; // Grey floor
            context.fillRect(0, 0, canvas.width, canvas.height);
            
            context.strokeStyle = '#ffcc00'; // Yellow safety line
            context.lineWidth = 5;
            context.strokeRect(50, 50, canvas.width - 100, canvas.height - 100);
            
            context.fillStyle = '#fff';
            context.font = '20px Arial';
            context.fillText("PATNA METRO STATION - PHASE 1", 100, 40);
        }

        function update() {
            player.x += moveX * 5;
            player.y += moveY * 5;
            
            context.clearRect(0, 0, canvas.width, canvas.height);
            drawMap();

            // Draw Player
            context.fillStyle = player.color;
            context.fillRect(player.x, player.y, player.size, player.size);
            
            requestAnimationFrame(update);
        }

        // Joystick Logic
        const knob = document.getElementById('joystick-knob');
        window.addEventListener('touchmove', (e) => {
            let touch = e.touches[0];
            let rect = document.getElementById('joystick-container').getBoundingClientRect();
            let dx = touch.clientX - (rect.left + 50);
            let dy = touch.clientY - (rect.top + 50);
            let dist = Math.sqrt(dx*dx + dy*dy);
            
            if (dist < 50) {
                knob.style.left = dx + 'px';
                knob.style.top = dy + 'px';
                moveX = dx / 50;
                moveY = dy / 50;
            }
        });
        window.addEventListener('touchend', () => {
            knob.style.left = '0px'; knob.style.top = '0px';
            moveX = 0; moveY = 0;
        });

        update();
    </script>
</body>
</html>

