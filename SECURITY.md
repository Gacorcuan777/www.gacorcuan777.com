<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Slot Machine Simulasi</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial, Helvetica, sans-serif;
}

body{
    background:linear-gradient(135deg,#1b1b1b,#3d3d3d);
    color:white;
    display:flex;
    justify-content:center;
    align-items:center;
    height:100vh;
}

.container{
    width:420px;
    background:#222;
    border-radius:15px;
    padding:25px;
    text-align:center;
    box-shadow:0 0 20px rgba(0,0,0,.5);
}

h1{
    margin-bottom:20px;
}

.reels{
    display:flex;
    justify-content:center;
    gap:15px;
    margin:25px 0;
}

.reel{
    width:90px;
    height:90px;
    background:white;
    color:black;
    font-size:55px;
    border-radius:12px;
    display:flex;
    align-items:center;
    justify-content:center;
}

button{
    background:#ff9800;
    color:white;
    border:none;
    padding:15px 30px;
    font-size:18px;
    border-radius:8px;
    cursor:pointer;
}

button:hover{
    background:#e68900;
}

#message{
    margin-top:20px;
    font-size:22px;
    font-weight:bold;
}

.score{
    margin-top:15px;
    font-size:20px;
}
</style>

</head>
<body>

<div class="container">

<h1>🎰 Slot Simulasi</h1>

<div class="reels">
<div class="reel" id="r1">🍒</div>
<div class="reel" id="r2">🍋</div>
<div class="reel" id="r3">⭐</div>
</div>

<button onclick="spin()">PUTAR</button>

<div id="message">Tekan tombol untuk bermain.</div>

<div class="score">
Skor : <span id="score">0</span>
</div>

</div>

<script>

const symbols=[
"🍒",
"🍋",
"⭐",
"🍇",
"🍊",
"🔔",
"💎",
"7️⃣"
];

let score=0;

function randomSymbol(){
    return symbols[Math.floor(Math.random()*symbols.length)];
}

function spin(){

const btn=document.querySelector("button");
btn.disabled=true;

let interval=setInterval(()=>{

document.getElementById("r1").innerHTML=randomSymbol();
document.getElementById("r2").innerHTML=randomSymbol();
document.getElementById("r3").innerHTML=randomSymbol();

},100);

setTimeout(()=>{

clearInterval(interval);

const s1=randomSymbol();
const s2=randomSymbol();
const s3=randomSymbol();

document.getElementById("r1").innerHTML=s1;
document.getElementById("r2").innerHTML=s2;
document.getElementById("r3").innerHTML=s3;

if(s1===s2 && s2===s3){

score+=100;
document.getElementById("message").innerHTML="🎉 Cocok! +100 Skor";

}else if(s1===s2 || s2===s3 || s1===s3){

score+=20;
document.getElementById("message").innerHTML="👍 Dua simbol sama! +20 Skor";

}else{

document.getElementById("message").innerHTML="😄 Belum cocok. Coba lagi.";

}

document.getElementById("score").innerHTML=score;

btn.disabled=false;

},1200);

}

</script>

</body>
</html>Gacorcuan777.com
