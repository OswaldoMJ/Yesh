<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>De mi para la que me dijo que no </title>
    <style>
        body {
            background-color: #ffebf0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            overflow: hidden;
            font-family: 'Arial', sans-serif;
            margin: 0;
        }

        .romantic-name {
            font-size: 50px;
            font-weight: bold;
            color: #ff3366;
            text-shadow: 2px 2px 10px rgba(255, 51, 102, 0.7);
            animation: heartbeat 1.5s infinite alternate ease-in-out;
            position: absolute;
            cursor: pointer;
            transition: top 0.2s, left 0.2s;
        }

        @keyframes heartbeat {
            0% { transform: scale(1); }
            100% { transform: scale(1.2); }
        }

        .heart {
            color: red;
            font-size: 30px;
            position: absolute;
            top: -10px;
            right: -30px;
            animation: float 1.5s infinite alternate ease-in-out;
        }

        @keyframes float {
            0% { transform: translateY(0); opacity: 1; }
            100% { transform: translateY(-10px); opacity: 0.8; }
        }
    </style>
</head>
<body>

    <div class="romantic-name" id="name" style="top: 50%; left: 50%;">
        💖 Yess tu me gustas mucho 💖
        <span class="heart">❤️</span>
    </div>

    <script>
        const nameElement = document.getElementById("name");

        document.addEventListener("mousemove", (event) => {
            const x = event.clientX;
            const y = event.clientY;
            const nameRect = nameElement.getBoundingClientRect();

            const nameX = nameRect.left + nameRect.width / 2;
            const nameY = nameRect.top + nameRect.height / 2;
            const distance = Math.sqrt((x - nameX) ** 2 + (y - nameY) ** 2);

            if (distance < 800) { // Si el cursor está cerca
                const moveX = (nameX - x) * 1;  // Movimiento inverso
                const moveY = (nameY - y) * 1;

                let newX = nameElement.offsetLeft + moveX;
                let newY = nameElement.offsetTop + moveY;

                // Limitar el movimiento dentro de la pantalla
                const maxX = window.innerWidth - nameRect.width;
                const maxY = window.innerHeight - nameRect.height;
                newX = Math.max(0, Math.min(maxX, newX));
                newY = Math.max(0, Math.min(maxY, newY));

                nameElement.style.left = `${newX}px`;
                nameElement.style.top = `${newY}px`;
            }
        });
    </script>

</body>
</html>
