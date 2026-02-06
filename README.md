# anushka-valentine
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Anushka ❤️</title>
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<style>
* { box-sizing: border-box; }

body {
  margin: 0;
  height: 100vh;
  background: linear-gradient(135deg, #ff9a9e, #fad0c4);
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: "Segoe UI", sans-serif;
  overflow: hidden;
}

.card {
  width: 90%;
  max-width: 380px;
  background: rgba(255,255,255,0.2);
  backdrop-filter: blur(10px);
  border-radius: 20px;
  padding: 25px;
  text-align: center;
  color: #fff;
  position: relative;
}

.heart {
  font-size: 55px;
  animation: beat 1s infinite;
}

@keyframes beat {
  0%,100% { transform: scale(1); }
  50% { transform: scale(1.3); }
}

h1 { margin: 10px 0; }

#message {
  min-height: 45px;
  font-size: 18px;
}

#emoji {
  font-size: 42px;
  margin: 10px 0;
}

.buttons {
  position: relative;
  height: 160px;
  margin-top: 15px;
}

button {
  padding: 12px 26px;
  font-size: 16px;
  border-radius: 25px;
  border: none;
  cursor: pointer;
  position: absolute;
}

#yesBtn {
  background: #ff3366;
  color: white;
  left: 20px;
  bottom: 10px;
}

#noBtn {
  background: #555;
  color: white;
  right: 20px;
  bottom: 10px;
}

#slide1, #slide2 {
  display: none;
}

#slide1 img {
  width: 100%;
  border-radius: 15px;
  margin-top: 15px;
}

#nextBtn {
  margin-top: 15px;
  background: #33cc66;
  color: white;
  padding: 12px 25px;
  border-radius: 25px;
  border: none;
  cursor: pointer;
}

.floating {
  position: absolute;
  font-size: 20px;
  animation: floatUp 2s forwards;
}

@keyframes floatUp {
  from { opacity: 1; transform: translateY(0); }
  to { opacity: 0; transform: translateY(-150px) scale(1.5); }
}
</style>
</head>

<body>

<div class="card">

  <div id="intro">
    <div class="heart">❤️</div>
    <h1>Anushka</h1>
    <div id="message">I have something special to ask you…</div>
    <div id="emoji">✨💖🌸</div>

    <div class="buttons" id="btnArea">
      <button id="yesBtn">Yes 💕</button>
      <button id="noBtn">No 🙈</button>
    </div>
  </div>

  <div id="slide1">
    <h2>You made my heart smile 💖</h2>
    <img src="https://images.unsplash.com/photo-1529626455594-4ff0802cfb7e?auto=format&fit=crop&w=800&q=80">
    <button id="nextBtn">Next ➡️</button>
  </div>

  <div id="slide2">
    <h2>💌 My Proposal 💌</h2>
    <p>You are the calm in my chaos ✨</p>
    <p>You make ordinary moments magical 💫</p>
    <p>Will you be my Valentine, Anushka? ❤️</p>
  </div>

</div>

<audio id="music" loop>
  <source src="https://www.bensound.com/bensound-music/bensound-love.mp3">
</audio>

<script>
const noBtn = document.getElementById("noBtn");
const yesBtn = document.getElementById("yesBtn");
const btnArea = document.getElementById("btnArea");
const message = document.getElementById("message");
const emoji = document.getElementById("emoji");
const music = document.getElementById("music");

const intro = document.getElementById("intro");
const slide1 = document.getElementById("slide1");
const slide2 = document.getElementById("slide2");
const nextBtn = document.getElementById("nextBtn");

let musicStarted = false;

const texts = [
  "Please think again 🥺",
  "My heart is waiting 💔",
  "One yes can change everything ❤️",
  "Don’t run away 🙈"
];

const emojis = ["🥺💖🌸", "✨😍💌", "💫🥰🌷"];

function startMusic() {
  if (!musicStarted) {
    music.play();
    musicStarted = true;
  }
}

function floatHeart(x, y) {
  const h = document.createElement("div");
  h.className = "floating";
  h.innerText = "💖";
  h.style.left = x + "px";
  h.style.top = y + "px";
  document.body.appendChild(h);
  setTimeout(() => h.remove(), 2000);
}

/* NO BUTTON */
noBtn.addEventListener("click", () => {
  startMusic();

  const maxX = btnArea.clientWidth - noBtn.offsetWidth;
  const maxY = btnArea.clientHeight - noBtn.offsetHeight;

  let x, y;
  do {
    x = Math.random() * maxX;
    y = Math.random() * maxY;
  } while (x < 80 && y > maxY - 60); // avoid Yes area

  noBtn.style.left = x + "px";
  noBtn.style.top = y + "px";

  message.innerText = texts[Math.floor(Math.random() * texts.length)];
  emoji.innerText = emojis[Math.floor(Math.random() * emojis.length)];

  floatHeart(window.innerWidth / 2, window.innerHeight / 2);
});

/* YES BUTTON */
yesBtn.addEventListener("click", () => {
  startMusic();
  intro.style.display = "none";
  slide1.style.display = "block";
});

/* NEXT BUTTON */
nextBtn.addEventListener("click", () => {
  slide1.style.display = "none"; 
  slide2.style.display = "block";
});
</script>

</body>
</html>
