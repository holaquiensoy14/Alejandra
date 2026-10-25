<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Para Alejandra ✨</title>
    <style>
        body, html {
            margin: 0; padding: 0;
            width: 100%; height: 100%;
            display: flex; justify-content: center; align-items: center;
            background-color: #fce4ec; /* Rosa inicial */
            font-family: 'Arial', sans-serif;
            overflow: hidden;
            transition: background 2s;
        }

        /* FONDO GALAXIA PROFUNDA */
        #galaxy {
            position: fixed; top: 0; left: 0; width: 100%; height: 100%;
            background: radial-gradient(circle at center, #1b2735 0%, #000 100%);
            display: none; z-index: -1;
        }

        .star {
            position: absolute; background: white; border-radius: 50%;
            animation: fall 2s linear infinite;
        }

        @keyframes fall {
            from { transform: translateY(-10vh); opacity: 1; }
            to { transform: translateY(110vh); opacity: 0; }
        }

        #container { text-align: center; width: 100%; z-index: 10; }
        .item { display: none; }

        /* IMAGEN DE FLORES REALES */
        .flores-reales {
            width: 250px; /* Tamaño grande */
            filter: drop-shadow(0 0 20px rgba(255, 192, 203, 0.8));
            animation: float 3s ease-in-out infinite;
        }

        @keyframes float {
            0%, 100% { transform: translateY(0); }
            50% { transform: translateY(-15px); }
        }

        /* ZOOM DEL CORAZÓN */
        .zoom-final {
            animation: zoomIn 1.5s forwards, heartbeat 0.8s infinite 1.5s;
        }

        @keyframes zoomIn {
            0% { transform: scale(0); opacity: 0; }
            100% { transform: scale(3.5); opacity: 1; }
        }

        @keyframes heartbeat {
            0%, 100% { transform: scale(3.5); }
            50% { transform: scale(3.8); }
        }

        #btn-next {
            background: #ff4081; color: white; border: none;
            padding: 15px 35px; border-radius: 50px; font-size: 20px;
            font-weight: bold; cursor: pointer; margin-top: 40px;
            box-shadow: 0 4px 15px rgba(255, 64, 129, 0.5);
            transition: 0.3s;
        }

        .texto { color: #ad1457; font-size: 28px; font-weight: bold; margin-top: 20px; text-shadow: 1px 1px 2px rgba(0,0,0,0.1); }
        .texto-final { color: white; font-size: 14px; margin-top: 40px; letter-spacing: 3px; font-weight: 100; opacity: 0.8; }
    </style>
</head>
<body>

    <div id="galaxy"></div>

    <div id="container">
        <div id="s1" class="item">
            <div style="font-size: 100px; animation: float 3s infinite;">🎁</div>
        </div>
        
        <div id="s2" class="item">
            <img src="https://i.ibb.co/Vp6qH8S/flowers-aesthetic.png" class="flores-reales" alt="Flores para Leslie">
            <div style="font-size: 50px; margin-top: -30px;">🍫</div>
            <div class="texto">Eres la mejor</div>
        </div>

        <div id="s3" class="item">
            <div id="heart" style="font-size: 80px; color: #ff1744; filter: drop-shadow(0 0 20px #ff0000);">❤️</div>
            <div class="texto-final" id="t-final">¡HERMOSA ALEJANDRA! ❤️</div>
        </div>

        <button id="btn-next">Toca aquí</button>
    </div>

    <audio id="player">
        <source src="https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3" type="audio/mpeg">
    </audio>

    <script>
        let paso = 0;
        const btn = document.getElementById('btn-next');
        const player = document.getElementById('player');

        function generarEstrellas() {
            const g = document.getElementById('galaxy');
            for(let i=0; i<80; i++) {
                let s = document.createElement('div');
                s.className = 'star';
                s.style.width = s.style.height = Math.random()*3+'px';
                s.style.left = Math.random()*100+'vw';
                s.style.animationDuration = (Math.random()*1.5 + 0.5)+'s';
                g.appendChild(s);
            }
        }

        btn.onclick = function() {
            paso++;
            player.play().catch(() => {});

            if(paso === 1) {
                document.getElementById('s1').style.display = 'block';
                btn.innerText = '¿Qué tiene dentro?';
            }
            else if(paso === 2) {
                document.getElementById('s1').style.display = 'none';
                document.getElementById('s2').style.display = 'block';
                btn.innerText = 'Falta algo...';
            }
            else if(paso === 3) {
                document.getElementById('s2').style.display = 'none';
                document.getElementById('s3').style.display = 'block';
                document.getElementById('heart').classList.add('zoom-final');
                
                // ACTIVAR GALAXIA
                document.getElementById('galaxy').style.display = 'block';
                document.body.style.background = '#000';
                generarEstrellas();
                
                btn.style.display = 'none';
            }
        };
    </script>
</body>
</html>
