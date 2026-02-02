[index.html.md](https://github.com/user-attachments/files/25018207/index.html.md)
#   
<!DOCTYPE html>  
<html lang="en">  
<head>  
<meta charset="UTF-8">  
<title>💘 Be My Valentine</title>  
  
<style>  
  body {  
    margin: 0;  
    height: 100vh;  
    overflow: hidden;  
    background: radial-gradient(circle at top, #ff758c, #ff7eb3);  
    font-family: 'Comic Sans MS', cursive, sans-serif;  
    display: flex;  
    justify-content: center;  
    align-items: center;  
  }  
  
  .card {  
    background: white;  
    padding: 40px;  
    border-radius: 25px;  
    text-align: center;  
    box-shadow: 0 25px 50px rgba(0,0,0,0.3);  
    width: 340px;  
    z-index: 10;  
  }  
  
  h1 {  
    color: #ff3366;  
    margin-bottom: 25px;  
  }  
  
  .buttons {  
    position: relative;  
    height: 80px;  
  }  
  
  button {  
    font-size: 18px;  
    padding: 12px 26px;  
    border-radius: 14px;  
    border: none;  
    cursor: pointer;  
    transition: transform 0.2s ease;  
  }  
  
  #yesBtn {  
    background: #ff3366;  
    color: white;  
  }  
  
  #noBtn {  
    background: #bbb;  
    color: #333;  
    position: absolute;  
  }  
  
  #result {  
    display: none;  
  }  
  
  img {  
    width: 100%;  
    border-radius: 18px;  
    margin-top: 20px;  
  }  
  
  .heart {  
    position: fixed;  
    bottom: -20px;  
    font-size: 24px;  
    animation: floatUp linear forwards;  
    pointer-events: none;  
  }  
  
  @keyframes floatUp {  
    from {  
      transform: translateY(0) rotate(0deg);  
      opacity: 1;  
    }  
    to {  
      transform: translateY(-120vh) rotate(360deg);  
      opacity: 0;  
    }  
  }  
  
  .explosion-heart {  
    position: fixed;  
    font-size: 26px;  
    pointer-events: none;  
    animation: explode 1.2s ease-out forwards;  
  }  
  
  @keyframes explode {  
    from {  
      transform: translate(0,0) scale(1);  
      opacity: 1;  
    }  
    to {  
      transform: translate(var(--x), var(--y)) scale(0.5);  
      opacity: 0;  
    }  
  }  
</style>  
</head>  
  
<body>  
  
<!-- 🎵 AUDIO -->  
<audio id="loveSong">  
  <source src="song.mp3" type="audio/mpeg">  
</audio>  
  
<div class="card" id="card">  
  <h1>Will you be my Valentine? 💖</h1>  
  <div class="buttons">  
    <button id="yesBtn">YES 💘</button>  
    <button id="noBtn">no 😐</button>  
  </div>  
</div>  
  
<div class="card" id="result">  
  <h1>💥💖 IT’S OFFICIAL 💖💥</h1>  
  <p>You are my Valentine now.</p>  
  <img src="valentine.jpg">  
</div>  
  
<script>  
  const noBtn = document.getElementById("noBtn");  
  const yesBtn = document.getElementById("yesBtn");  
  const card = document.getElementById("card");  
  const result = document.getElementById("result");  
  const song = document.getElementById("loveSong");  
  
  let yesScale = 1;  
  
  function moveNoButton() {  
    const x = Math.random() * 260 - 130;  
    const y = Math.random() * 140 - 70;  
    noBtn.style.transform = `translate(${x}px, ${y}px)`;  
  
    yesScale += 0.12;  
    yesBtn.style.transform = `scale(${yesScale})`;  
  }  
  
  noBtn.addEventListener("mouseover", moveNoButton);  
  noBtn.addEventListener("click", moveNoButton);  
  
  // floating hearts  
  function createHeart() {  
    const heart = document.createElement("div");  
    heart.className = "heart";  
    heart.textContent = "💖";  
  
    heart.style.left = Math.random() * 100 + "vw";  
    heart.style.animationDuration = Math.random() * 3 + 4 + "s";  
    heart.style.fontSize = Math.random() * 20 + 20 + "px";  
  
    document.body.appendChild(heart);  
    setTimeout(() => heart.remove(), 7000);  
  }  
  
  setInterval(createHeart, 250);  
  
  function explodeHearts() {  
    for (let i = 0; i < 60; i++) {  
      const heart = document.createElement("div");  
      heart.className = "explosion-heart";  
      heart.textContent = "💖";  
  
      heart.style.setProperty("--x", (Math.random() - 0.5) * 600 + "px");  
      heart.style.setProperty("--y", (Math.random() - 0.5) * 600 + "px");  
  
      heart.style.left = "50vw";  
      heart.style.top = "50vh";  
  
      document.body.appendChild(heart);  
      setTimeout(() => heart.remove(), 1200);  
    }  
  }  
  
 yesBtn.addEventListener("click", () => {  
  song.currentTime = 30; // ⬅️ CHANGE THIS NUMBER (seconds)  
  song.play();  
  
  explodeHearts();  
  
  setTimeout(() => {  
    card.style.display = "none";  
    result.style.display = "block";  
  }, 600);  
});  
</script>  
  
</body>  
</html>  
