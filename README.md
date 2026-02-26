# Invite
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Princess G (bobo🐷) 👑</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600&display=swap" rel="stylesheet">

<style>
body{
  margin:0;
  font-family:'Poppins',sans-serif;
  background: linear-gradient(135deg,#d6ecff,#ffd6f0);
  overflow-x:hidden;
  scroll-behavior:smooth;
  color:#444;
}

section{
  min-height:100vh;
  display:flex;
  flex-direction:column;
  justify-content:center;
  align-items:center;
  padding:40px;
  text-align:center;
}

h1{
  font-size:3em;
  background:linear-gradient(45deg,#ff8fd8,#8ecbff);
  -webkit-background-clip:text;
  -webkit-text-fill-color:transparent;
}

.glass{
  background:rgba(255,255,255,0.4);
  backdrop-filter:blur(15px);
  padding:30px;
  border-radius:25px;
  box-shadow:0 10px 40px rgba(0,0,0,0.1);
}

button{
  padding:12px 25px;
  border:none;
  border-radius:30px;
  background:#ff9edb;
  color:white;
  cursor:pointer;
  font-weight:600;
  margin-top:20px;
  transition:0.3s;
}
button:hover{
  transform:scale(1.1);
  background:#ff75c7;
}

.gallery img{
  width:220px;
  margin:10px;
  border-radius:20px;
  box-shadow:0 10px 25px rgba(0,0,0,0.2);
  transition:0.4s;
}
.gallery img:hover{
  transform:scale(1.1);
}

#countdown{
  font-size:2em;
  margin-top:20px;
}

.puzzle{
  width:300px;
  height:300px;
  display:grid;
  grid-template-columns:repeat(3,1fr);
  gap:2px;
}

.piece{
  background-image:url('your-photo.jpg');
  background-size:300px 300px;
  cursor:grab;
}

.hidden{display:none;}

footer{
  padding:20px;
  font-size:14px;
}
</style>
</head>

<body>

<!-- Music -->
<audio id="bgMusic" loop>
  <source src="your-song.mp3" type="audio/mpeg">
</audio>
<button onclick="toggleMusic()" style="position:fixed;top:20px;right:20px;">🎵</button>

<!-- Slide 1 -->
<section>
<h1>For My Princess G (bobo🐷) 👑</h1>
<div class="glass">
<p>You are not just special… you are royal in my world.</p>
<button onclick="document.getElementById('memories').scrollIntoView()">Enter Your Kingdom ✨</button>
</div>
</section>

<!-- Memories -->
<section id="memories">
<h1>Memories We Treasure 💭</h1>
<div class="gallery">
<img src="pic1.jpg">
<img src="pic2.jpg">
<img src="pic3.jpg">
</div>
</section>

<!-- Messages -->
<section>
<h1>Our Silly Royal Book 💌</h1>
<div class="glass">
<p>👑 My queen of random mood swings.</p>
<p>🐷 The only person who can bully me and still be cute.</p>
<p>💖 Even silence with you feels magical.</p>
<p>✨ You are my forever favorite notification.</p>
</div>
</section>

<!-- Countdown -->
<section>
<h1>Countdown to Your Crown Day 🎂</h1>
<div id="countdown"></div>
</section>

<!-- Puzzle -->
<section>
<h1>Unlock the Royal Surprise 🧩</h1>
<div class="puzzle" id="puzzle"></div>
<button id="surpriseBtn" class="hidden" onclick="celebrate()">Reveal Surprise 👑</button>
</section>

<footer>
Made with infinite love 💗
</footer>

<script>
function toggleMusic(){
  let music=document.getElementById("bgMusic");
  music.paused?music.play():music.pause();
}

// Countdown
const birthday=new Date("2026-05-20 00:00:00").getTime();
setInterval(()=>{
  let now=new Date().getTime();
  let gap=birthday-now;
  let d=Math.floor(gap/(1000*60*60*24));
  let h=Math.floor((gap%(1000*60*60*24))/(1000*60*60));
  let m=Math.floor((gap%(1000*60*60))/(1000*60));
  let s=Math.floor((gap%(1000*60))/1000);
  document.getElementById("countdown").innerHTML=
  `${d}d ${h}h ${m}m ${s}s`;
},1000);

// Puzzle
const puzzle=document.getElementById("puzzle");
let correct=0;

for(let i=0;i<9;i++){
  let piece=document.createElement("div");
  piece.classList.add("piece");
  piece.style.backgroundPosition=`${-100*(i%3)}px ${-100*Math.floor(i/3)}px`;
  piece.draggable=true;

  piece.ondragstart=(e)=>{
    e.dataTransfer.setData("text/plain",i);
  };

  piece.ondragover=(e)=>e.preventDefault();

  piece.ondrop=(e)=>{
    e.preventDefault();
    correct++;
    piece.style.opacity="0.6";
    if(correct===9){
      document.getElementById("surpriseBtn").classList.remove("hidden");
    }
  };

  puzzle.appendChild(piece);
}

function celebrate(){
  alert("You are my once-in-a-lifetime love 👑💖");
  document.body.style.background="linear-gradient(135deg,#ffb3e6,#a0d8ff)";
}
</script>

</body>
</html>
