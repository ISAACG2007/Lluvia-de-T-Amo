<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<title>Lluvia de Te Amo</title>
<style>
    body {
        margin: 0;
        background: black;
        overflow: hidden;
    }
    canvas {
        display: block;
    }
</style>
</head>
<body>
<canvas id="teAmoCanvas"></canvas>

<script>
    const canvas = document.getElementById('teAmoCanvas');
    const ctx = canvas.getContext('2d');

    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    const letters = ["TE AMO DANI"];
    const fontSize = 20;
    const columns = Math.floor(canvas.width / fontSize);

    const drops = [];
    for (let x = 0; x < columns; x++) {
        drops[x] = Math.random() * -100; // posición inicial aleatoria
    }

    function draw() {
        ctx.fillStyle = "rgba(0, 0, 0, 0.05)"; // efecto de rastro
        ctx.fillRect(0, 0, canvas.width, canvas.height);

        ctx.fillStyle = "#ff4da6"; // rosa fuerte
        ctx.font = fontSize + "px Arial";

        for (let i = 0; i < drops.length; i++) {
            const text = letters[0];
            ctx.fillText(text, i * fontSize, drops[i] * fontSize);

            if (drops[i] * fontSize > canvas.height && Math.random() > 0.975) {
                drops[i] = 0;
            }
            drops[i]++;
        }
    }

    setInterval(draw, 80);

    window.addEventListener("resize", () => {
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
    });
</script>
</body>
</html>
