<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Happy Birthday ❤️</title>

<!-- Google Font -->
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">

<style>
:root {
    --bg: #0f0f1a;
    --accent: #ff4d6d;
    --soft: #1a1a2e;
    --text: #f1f1f1;
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
}

body {
    background: var(--bg);
    color: var(--text);
    overflow-x: hidden;
}

/* Floating particles */
canvas {
    position: fixed;
    top: 0;
    left: 0;
    z-index: -1;
}

/* Sections */
section {
    min-height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    text-align: center;
    padding: 40px;
    opacity: 0;
    transform: translateY(50px);
    transition: all 1s ease;
}

section.visible {
    opacity: 1;
    transform: translateY(0);
}

/* Hero */
.hero h1 {
    font-size: 3rem;
    background: linear-gradient(45deg, #ff4d6d, #ff9a9e);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    animation: glow 2s infinite alternate;
}

@keyframes glow {
    from { text-shadow: 0 0 10px #ff4d6d; }
    to { text-shadow: 0 0 25px #ff4d6d; }
}

.hero button {
    margin-top: 30px;
    padding: 12px 25px;
    border: none;
    border-radius: 30px;
    background: var(--accent);
    color: white;
    cursor: pointer;
    transition: 0.3s;
}

.hero button:hover {
    transform: scale(1.1);
}

/* Card style */
.card {
    background: var(--soft);
    padding: 30px;
    border-radius: 20px;
    max-width: 500px;
    box-shadow: 0 0 30px rgba(255, 77, 109, 0.2);
}

/* Photo gallery */
.gallery img {
    width: 200px;
    border-radius: 15px;
    margin: 10px;
    transition: 0.4s;
}

.gallery img:hover {
    transform: scale(1.1) rotate(2deg);
}

/* Final message */
.final h2 {
    font-size: 2.5rem;
    margin-bottom: 20px;
}

/* Floating hearts */
.heart {
    position: fixed;
    color: #ff4d6d;
    animation: floatUp 5s linear infinite;
}

@keyframes floatUp {
    from {
        transform: translateY(100vh);
        opacity: 1;
    }
    to {
        transform: translateY(-10vh);
        opacity: 0;
    }
}
</style>
</head>

<body>

<canvas id="bg"></canvas>

<!-- HERO -->
<section class="hero visible">
    <h1>Happy Birthday ❤️</h1>
    <p>Today is all about you...</p>
    <button onclick="scrollNext()">Start the Journey</button>
</section>

<!-- MESSAGE -->
<section>
    <div class="card">
        <h2>To Someone Special</h2>
        <p>
            On this beautiful day, I just want you to know how much you mean to me.
            You bring light, happiness, and warmth into my life in ways I can’t even explain.
        </p>
    </div>
</section>

<!-- MEMORIES -->
<section>
    <div class="card">
        <h2>Memories 💭</h2>
        <p>
            Every moment with you feels like magic.
            The laughs, the talks, the little things… they all matter more than you know.
        </p>
    </div>
</section>

<!-- GALLERY -->
<section>
    <h2>Our Moments 📸</h2>
    <div class="gallery">
        <img src="https://picsum.photos/200?1">
        <img src="https://picsum.photos/200?2">
        <img src="https://picsum.photos/200?3">
    </div>
</section>

<!-- FINAL -->
<section class="final">
    <h2>I Hope You Smile Today 😊</h2>
    <p>
        You deserve all the happiness in the world.
        And I’ll always be here, cheering for you, caring for you… ❤️
    </p>
</section>

<script>
/* Scroll reveal */
const sections = document.querySelectorAll("section");

window.addEventListener("scroll", () => {
    sections.forEach(sec => {
        const top = sec.getBoundingClientRect().top;
        if (top < window.innerHeight - 100) {
            sec.classList.add("visible");
        }
    });
});

function scrollNext() {
    window.scrollTo({
        top: window.innerHeight,
        behavior: "smooth"
    });
}

/* Floating hearts */
setInterval(() => {
    const heart = document.createElement("div");
    heart.className = "heart";
    heart.innerHTML = "❤";
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.fontSize = Math.random() * 20 + 10 + "px";
    document.body.appendChild(heart);

    setTimeout(() => heart.remove(), 5000);
}, 500);

/* Particle background */
const canvas = document.getElementById("bg");
const ctx = canvas.getContext("2d");

canvas.width = window.innerWidth;
canvas.height = window.innerHeight;

let particles = [];

for (let i = 0; i < 80; i++) {
    particles.push({
        x: Math.random() * canvas.width,
        y: Math.random() * canvas.height,
        r: Math.random() * 2,
        d: Math.random() * 1
    });
}

function draw() {
    ctx.clearRect(0, 0, canvas.width, canvas.height);
    ctx.fillStyle = "#ff4d6d";

    particles.forEach(p => {
        ctx.beginPath();
        ctx.arc(p.x, p.y, p.r, 0, Math.PI * 2);
        ctx.fill();
    });

    update();
}

function update() {
    particles.forEach(p => {
        p.y += p.d;
        if (p.y > canvas.height) {
            p.y = 0;
            p.x = Math.random() * canvas.width;
        }
    });
}

setInterval(draw, 30);
</script>

</body>
</html>
