# for-pari
<!doctype html>
<html>
<head>
<meta charset="utf-8">
<title>Untitled Document</title>
</head>

<body>
</body>
</html><!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
<title>For Pari — Love Website</title>

<!-- Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Great+Vibes&family=Inter:wght@300;400;700&display=swap" rel="stylesheet">

<style>
    :root {
        --pink:#ff4da6;
        --light:#ffeef8;
        --bg1:#fff0f6;
        --bg2:#fff7fb;
    }

    * { box-sizing: border-box; }

    body {
        margin:0;
        font-family:'Inter', sans-serif;
        height:100vh;
        background: linear-gradient(135deg, var(--bg1), var(--bg2));
        display:flex;
        justify-content:center;
        align-items:center;
        padding:20px;
        overflow:hidden;
    }

    .card {
        width:900px;
        max-width:95vw;
        background:rgba(255,255,255,0.85);
        padding:30px;
        border-radius:20px;
        box-shadow:0 8px 30px rgba(255,0,120,0.2);
        position:relative;
        backdrop-filter:blur(8px);
    }

    header { display:flex; gap:20px; align-items:center; }

    .logo {
        width:100px; height:100px;
        border-radius:50%;
        background: radial-gradient(circle at 30% 30%, white, var(--pink));
        display:flex;
        justify-content:center;
        align-items:center;
        box-shadow:0 6px 16px rgba(255,77,160,0.3);
    }

    h1 {
        font-family:'Great Vibes', cursive;
        font-size:48px;
        margin:0;
    }

    p.lead {
        margin:5px 0;
        color:#5b2840;
        font-size:16px;
    }

    .controls { margin-top:10px; display:flex; gap:10px; }

    .btn {
        padding:10px 16px;
        border-radius:10px;
        border:none;
        cursor:pointer;
        font-weight:600;
        font-size:14px;
    }

    .btn-primary { background:var(--pink); color:white; }
    .btn-ghost { background:transparent; border:2px solid rgba(255,77,160,0.2); }

    .quotes {
        margin-top:20px;
        display:grid;
        grid-template-columns:repeat(2,1fr);
        gap:15px;
    }

    .quote {
        background:rgba(255,240,252,0.7);
        padding:20px;
        border-radius:14px;
        text-align:center;
        font-size:16px;
        color:#3e1030;
        box-shadow:0 4px 12px rgba(255,80,150,0.12);
    }

    footer {
        margin-top:25px;
        display:flex;
        justify-content:space-between;
        color:#6a2b3f;
        font-size:14px;
    }

    /* floating hearts */
    .heart {
        position:absolute;
        width:28px;
        height:28px;
        opacity:0.9;
    }

    @keyframes floatUp {
        0% { transform:translateY(0) scale(0.6); opacity:0; }
        10%{ opacity:1; }
        100% { transform:translateY(-450px) scale(1); opacity:0; }
    }

    .center-heart {
        position:absolute;
        right:30px;
        top:20px;
        width:70px;
        animation:beat 1s infinite;
    }

    @keyframes beat {
        0%{transform:scale(1)}
        50%{transform:scale(1.1)}
        100%{transform:scale(1)}
    }

    @media (max-width:720px) {
        .quotes { grid-template-columns:1fr; }
        h1 { font-size:36px; }
    }
</style>
</head>

<body>

<div class="card" id="card">

    <!-- pulsing heart -->
    <div class="center-heart">
        ❤️
    </div>

    <header>
        <div class="logo">💗</div>
        <div>
            <h1>For Pari</h1>
            <p class="lead">A small place on the web made for the beauty of her eyes ✨</p>

            <div class="controls">
                <button class="btn btn-primary" id="playBtn">Play / Pause Music</button>
                <button class="btn btn-ghost" id="toggleHearts">Toggle Hearts</button>
            </div>
        </div>
    </header>

    <div class="quotes">
        <div class="quote">"In the quiet of your glance, I find my favorite story."</div>
        <div class="quote">"Her eyes are constellations—every look a universe."</div>
        <div class="quote">"I could get lost forever in the ocean of her eyes."</div>
        <div class="quote">"Those eyes hold the softest sunrise—warm and beautiful."</div>
        <div class="quote">"Her gaze speaks a language only my heart understands."</div>
        <div class="quote">"Her eyes make ordinary moments sacred."</div>
    </div>

    <footer>
        <span>Made with love — For Pari 💞</span>
        <span>💌</span>
    </footer>
</div>

<!-- Background music -->
<audio id="bgm" loop>
    <source src="music.mp3" type="audio/mpeg">
</audio>

<script>
    const card = document.getElementById('card');
    let heartsEnabled = true;

    function createHeart() {
        if (!heartsEnabled) return;

        const heart = document.createElement('div');
        heart.className = 'heart';
        const size = Math.random() * 25 + 20;

        heart.style.width = size + "px";
        heart.style.height = size + "px";
        heart.style.left = Math.random() * 90 + "%";
        heart.style.bottom = "-40px";
        heart.style.opacity = Math.random() * 0.4 + 0.6;
        heart.innerHTML = "💗";
        heart.style.fontSize = size + "px";
        heart.style.position = "absolute";
        heart.style.animation = `floatUp ${6 + Math.random()*4}s linear forwards`;

        card.appendChild(heart);

        setTimeout(() => heart.remove(), 12000);
    }

    let interval = setInterval(createHeart, 700);

    document.getElementById("toggleHearts").onclick = () => {
        heartsEnabled = !heartsEnabled;
        if (heartsEnabled) interval = setInterval(createHeart, 700);
        else clearInterval(interval);
    };

    // Music Controls
    const bgm = document.getElementById("bgm");
    let playing = false;

    document.getElementById("playBtn").onclick = () => {
        if (playing) {
            bgm.pause();
            playing = false;
        } else {
            bgm.play();
            playing = true;
        }
    };
</script>

</body>
</html>

