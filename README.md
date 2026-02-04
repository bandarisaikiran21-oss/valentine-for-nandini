index1.html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For Nandini 💖</title>

<style>
body {
    margin: 0;
    height: 100vh;
    background: linear-gradient(
        -45deg,
        #ff9a9e,
        #fad0c4,
        #fbc2eb,
        #a6c1ee
    );
    background-size: 400% 400%;
    animation: romanticBg 12s ease infinite;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: Arial, sans-serif;
    overflow: hidden;
}

@keyframes romanticBg {
    0% { background-position: 0% 50%; }
    50% { background-position: 100% 50%; }
    100% { background-position: 0% 50%; }
}




/* Main card */
.box {
    background: rgba(255,255,255,0.25);
    padding: 30px;
    border-radius: 25px;
    width: 85%;
    max-width: 360px;
    text-align: center;
    color: #fff;
    z-index: 2;
}

button {
    margin: 15px;
    padding: 12px 30px;
    font-size: 18px;
    border: none;
    border-radius: 30px;
    cursor: pointer;
}

#yes {
    background: #ff4d6d;
    color: white;
}

#no {
    background: white;
    color: #ff4d6d;
    position: absolute;
}

/* Floating hearts */
.floating-heart {
    position: fixed;
    bottom: -20px;
    pointer-events: none;
    animation: floatUp 6s linear forwards;
    z-index: 1;
}

@keyframes floatUp {
    0% {
        transform: translateY(0) scale(1);
        opacity: 1;
    }
    100% {
        transform: translateY(-110vh) scale(1.4);
        opacity: 0;
    }
}

/* Popup */
.popup {
    position: fixed;
    inset: 0;
    background: rgba(0,0,0,0.7);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 5;
}

/* Heart animation */
.heart-wrapper {
    position: relative;
    width: 280px;
    height: 280px;
    animation: zoomIn 0.6s ease-out forwards;
}

@keyframes zoomIn {
    from { transform: scale(0); }
    to { transform: scale(1); }
}

.heart {
    position: absolute;
    width: 180px;
    height: 180px;
    background: #ff4d6d;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%) rotate(-45deg);
}

.heart::before,
.heart::after {
    content: "";
    position: absolute;
    width: 180px;
    height: 180px;
    background: #ff4d6d;
    border-radius: 50%;
}

.heart::before {
    top: -90px;
    left: 0;
}

.heart::after {
    left: 90px;
    top: 0;
}

/* Text over heart */
.text-layer {
    position: absolute;
    inset: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-align: center;
    pointer-events: none;
}

.text-layer h2 {
    margin: 0;
    font-size: 26px;
    color: #fff;
    font-weight: 900;
    text-shadow: 0 3px 6px rgba(0,0,0,0.4);
}

.text-layer p {
    margin-top: 10px;
    font-size: 16px;
    color: #fff;
    font-style: italic;
    text-shadow: 0 2px 4px rgba(0,0,0,0.4);
}
</style>
</head>

<body>

<!-- Romantic music -->
<audio autoplay loop>
    <source src="https://cdn.pixabay.com/download/audio/2022/03/15/audio_7c0b3f0fa2.mp3" type="audio/mpeg">
</audio>

<div class="box" id="content">
    <h2>Hi Nandini 💖</h2>
    <p>I made something cute… just for you 😌</p>
    <button id="yes" onclick="openHeart()">Open my heart ❤️</button>
</div>

<script>
/* Floating hearts generator */
setInterval(() => {
    const heart = document.createElement("div");
    heart.className = "floating-heart";
    heart.innerHTML = ["💖","💕","💗","💘"][Math.floor(Math.random() * 4)];
    heart.style.left = Math.random() * 100 + "vw";
    heart.style.fontSize = (Math.random() * 14 + 16) + "px";
    document.body.appendChild(heart);
    setTimeout(() => heart.remove(), 6000);
}, 350);

/* App flow */
function openHeart() {
    content.innerHTML = `
        <p>From the moment we started talking, you made me smile in ways i didn't expect 😄</p>
        <p><strong>Will you be my Valentine? 💌</strong></p>
        <button id="yes" onclick="valentineYes()">YES ❤️</button>
        <button id="no" onmouseover="moveNo()">NO 😜</button>
    `;
}

function moveNo() {
    no.style.left = Math.random() * (innerWidth - 100) + "px";
    no.style.top = Math.random() * (innerHeight - 100) + "px";
}

function valentineYes() {
    content.innerHTML = `
        <h2>One more thing… 😳</h2>
        <p><strong>Will you marry me? 💍</strong></p>
        <button id="yes" onclick="marryYes()">YES 💖</button>
    `;
}

function marryYes() {
    const popup = document.createElement("div");
    popup.className = "popup";
    popup.innerHTML = `
        <div class="heart-wrapper">
            <div class="heart"></div>
            <div class="text-layer">
                <h2>Sai Kiran ❤️ Nandini</h2>
                <p>Forever starts now ✨</p>
            </div>
        </div>
    `;
    document.body.appendChild(popup);
}
</script>

</body>
</html>
