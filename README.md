<!DOCTYPE html>
<html>
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>MLovely - Patna Metro</title>
    <style>
        body, html { margin: 0; padding: 0; overflow: hidden; background: #1a1a1a; height: 100%; width: 100%; touch-action: none; font-family: 'Arial', sans-serif; }
        
        /* ML Intertwined Logo */
        #logo { position: absolute; top: 10px; left: 10px; font-size: 26px; font-weight: bold; color: #ff4500; z-index: 20; }
        #logo span { color: #fff; margin-left: -10px; }

        #ui { position: absolute; top: 15px; width: 100%; text-align: center; color: yellow; z-index: 10; pointer-events: none; }
        
        #player { position: absolute; width: 40px; height: 40px; background: #00ffff; border: 2px solid #fff; border-radius: 5px; box-shadow: 0 0 15px #00ffff; z-index: 5; }

        /* Joystick */
        #joystick-base { position: absolute; bottom: 40px; left: 40px; width: 90px; height: 90px; background: rgba(255,255,255,0.1); border: 2px solid #fff; border-radius: 50%; }
        #stick { position: absolute; top: 20px; left: 20px; width: 50px; height: 50px; background: red; border-radius: 50%; }

        /* Attack Button */
        #fire-btn { position: absolute; bottom: 50px; right: 50px; width: 70px; height: 70px; background: rgba(255,0,0,0.5); border: 3px solid #fff; border-radius: 50%; color: white; font-weight: bold; display: flex; align-items: center; justify-content: center; z-index: 20; }
    </style>
</head>
<body>
    <div id="logo">M<span>L</span>ovely</div>
    
    <div id="ui">
        <h3 style="margin:0;">PATNA METRO - HARINAGAR</h3>
        <p id="msg" style="color: #00ff00; margin:2px; font-size:14px;">Swaagat ba Patna Metro mein!</p>
    </div>

    <div id="player"></div>
    <div id="joystick-base"><div id="stick"></div></div>
    <div id="fire-btn" onclick="fire()">FIRE</div>

    <script>
        const player = document.getElementById('player');
        const stick = document.getElementById('stick');
        const base = document.getElementById('joystick-base');
        const msg = document.getElementById('msg');

        let px = window.innerWidth / 2, py = window.innerHeight / 2;
        let mx = 0, my = 0;
        let active = false;

        // Fire Function (Gun sound effect ke liye)
        function fire() {
            msg.innerText = "DHAYEN! DHAYEN!"; // Bhojpuri gun sound effect
            msg.style.color = "red";
            setTimeout(() => { 
                msg.innerText = "Swaagat ba Patna Metro mein!"; 
                msg.style.color = "#00ff00";
            }, 500);
        }

        const handleMove = (e) => {
            if (!active) return;
            const t = e.touches[0];
            const r = base.getBoundingClientRect();
            const dx = t.clientX - (r.left + 45), dy = t.clientY - (r.top + 45);
            const d = Math.min(Math.sqrt(dx*dx + dy*dy), 35);
            const a = Math.atan2(dy, dx);
            stick.style.transform = `translate(${Math.cos(a)*d}px, ${Math.sin(a)*d}px)`;
            mx = Math.cos(a) * (d / 7); my = Math.sin(a) * (d / 7);
        };

        base.addEventListener('touchstart', (e) => { active = true; handleMove(e); });
        window.addEventListener('touchmove', handleMove, { passive: false });
        window.addEventListener('touchend', () => { active = false; mx = 0; my = 0; stick.style.transform = 'translate(0,0)'; });

        function loop() {
            px = Math.max(0, Math.min(window.innerWidth - 40, px + mx));
            py = Math.max(0, Math.min(window.innerHeight - 40, py + my));
            player.style.left = px + 'px'; player.style.top = py + 'px';
            requestAnimationFrame(loop);
        }
        loop();
    </script>
</body>
</html>












