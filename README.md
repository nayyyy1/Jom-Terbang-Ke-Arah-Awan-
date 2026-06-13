# Jom-Terbang-Ke-Arah-Awan-
Main sambil belajar! Kuasai kemahiran memadan huruf Rumi ke Jawi dengan cara yang paling seronok. Permainan interaktif ini direka khas untuk membantu anda mengenali, mengingat, dan mengukuhkan padanan huruf dengan mudah. Sesuai untuk semua peringkat umur!
<!DOCTYPE html>
<html lang="ms">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Terbang ke arah Awan yang Tepat!</title>

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:Comic Sans MS,sans-serif;
}

body{
overflow:hidden;
}

#game{
width:100vw;
height:100vh;
position:relative;
background-size:cover;
background-position:center;
}

.level1{background:url("https://images.unsplash.com/photo-1506744038136-46273834b3fb") center/cover;}
.level2{background:url("https://images.unsplash.com/photo-1500530855697-b586d89ba3ee") center/cover;}
.level3{background:url("https://images.unsplash.com/photo-1502082553048-f009c37129b9") center/cover;}
.level4{background:url("https://images.unsplash.com/photo-1511497584788-876760111969") center/cover;}
.level5{background:url("https://images.unsplash.com/photo-1501785888041-af3ef285b470") center/cover;}
.level6{background:url("https://images.unsplash.com/photo-1441974231531-c6227db76b6e") center/cover;}
.level7{background:url("https://images.unsplash.com/photo-1470770841072-f978cf4d019e") center/cover;}
.level8{background:url("https://images.unsplash.com/photo-1469474968028-56623f02e42e") center/cover;}
.level9{background:url("https://images.unsplash.com/photo-1507525428034-b723cf961d3e") center/cover;}
.level10{background:url("https://images.unsplash.com/photo-1439066615861-d1af74d74000") center/cover;}

#title{
position:absolute;
top:10px;
width:100%;
text-align:center;
font-size:34px;
font-weight:bold;
color:white;
text-shadow:2px 2px 5px black;
}

#bird{
position:absolute;
bottom:120px;
left:50%;
transform:translateX(-50%);
font-size:80px;
transition:.4s;
}

#paper{
position:absolute;
bottom:180px;
left:50%;
transform:translateX(-50%);
background:white;
padding:10px 20px;
border-radius:10px;
font-size:35px;
font-weight:bold;
}

.cloud{
position:absolute;
top:120px;
width:180px;
height:120px;
background:white;
border-radius:60px;
display:flex;
justify-content:center;
align-items:center;
font-size:45px;
font-weight:bold;
}

.left{left:5%;}
.middle{left:40%;}
.right{right:5%;}

#score{
position:absolute;
top:70px;
left:20px;
background:white;
padding:10px;
border-radius:10px;
}

#noteBtn{
position:absolute;
top:20px;
right:20px;
padding:10px 20px;
}

#note{
display:none;
position:absolute;
width:90%;
height:80%;
top:10%;
left:5%;
background:white;
overflow:auto;
padding:20px;
border-radius:20px;
z-index:999;
}

#startScreen,
#endScreen{
position:absolute;
width:100%;
height:100%;
background:rgba(0,0,0,0.8);
display:flex;
justify-content:center;
align-items:center;
flex-direction:column;
color:white;
z-index:1000;
}

button{
padding:12px 20px;
font-size:18px;
margin:10px;
}

input{
padding:10px;
font-size:18px;
}

</style>
</head>

<body>

<div id="game" class="level1">

<div id="title">🕊️ Terbang ke arah Awan yang Tepat!</div>

<div id="score">Pusingan: 1/7 | Level: 1</div>

<button id="noteBtn">📖 Nota Jawi</button>

<div id="paper"></div>

<div id="bird">🐦</div>

<div class="cloud left" id="c1"></div>
<div class="cloud middle" id="c2"></div>
<div class="cloud right" id="c3"></div>

<div id="note">

<h2>Padanan Huruf Rumi ke Jawi</h2>

<table border="1" width="100%">
<tr>
<th>Rumi</th>
<th>Jawi</th>
</tr>

<tr><td>A</td><td>ا</td></tr>
<tr><td>B</td><td>ب</td></tr>
<tr><td>C</td><td>چ</td></tr>
<tr><td>D</td><td>د</td></tr>
<tr><td>F</td><td>ف</td></tr>
<tr><td>G</td><td>ݢ</td></tr>
<tr><td>J</td><td>ج</td></tr>
<tr><td>L</td><td>ل</td></tr>
<tr><td>M</td><td>م</td></tr>
<tr><td>N</td><td>ن</td></tr>
<tr><td>P</td><td>ڤ</td></tr>
<tr><td>Q</td><td>ق</td></tr>
<tr><td>R</td><td>ر</td></tr>
<tr><td>W</td><td>و</td></tr>
<tr><td>Y</td><td>ي</td></tr>
<tr><td>Z</td><td>ز</td></tr>

</table>

<button onclick="document.getElementById('note').style.display='none'">
Tutup
</button>

</div>

<div id="startScreen">

<h1>Selamat Datang!</h1>

<input id="playerName" placeholder="Masukkan nama anda">

<button onclick="startGame()">
Mula Bermain
</button>

</div>

<div id="endScreen" style="display:none">

<h1 id="message"></h1>

<h2>🐛 Burung mendapat hadiah cacing!</h2>

<button onclick="restartGame()">
Main Semula
</button>

<button onclick="nextLevel()">
Level Seterusnya
</button>

</div>

</div>

<script>

const pairs = {
"A":"ا",
"B":"ب",
"C":"چ",
"D":"د",
"F":"ف",
"G":"ݢ",
"J":"ج",
"L":"ل",
"M":"م",
"N":"ن",
"P":"ڤ",
"Q":"ق",
"R":"ر",
"W":"و",
"Y":"ي",
"Z":"ز"
};

let round=1;
let level=1;
let currentLetter;

function startGame(){
document.getElementById("startScreen").style.display="none";
newRound();
}

function randomLetter(){
let keys=Object.keys(pairs);
return keys[Math.floor(Math.random()*keys.length)];
}

function newRound(){

currentLetter=randomLetter();

paper.innerHTML=currentLetter;

let correct=pairs[currentLetter];

let values=Object.values(pairs);

values=values.sort(()=>Math.random()-0.5);

let options=[correct];

while(options.length<3){
let r=values[Math.floor(Math.random()*values.length)];
if(!options.includes(r)) options.push(r);
}

options=options.sort(()=>Math.random()-0.5);

c1.innerHTML=options[0];
c2.innerHTML=options[1];
c3.innerHTML=options[2];

c1.dataset.correct=options[0]==correct;
c2.dataset.correct=options[1]==correct;
c3.dataset.correct=options[2]==correct;

score.innerHTML=
`Pusingan: ${round}/7 | Level: ${level}`;
}

function choose(cloud){

if(cloud.dataset.correct=="true"){

round++;

if(round>7){
finishLevel();
}
else{
newRound();
}

}
else{
alert("Cuba lagi!");
}

}

c1.onclick=()=>choose(c1);
c2.onclick=()=>choose(c2);
c3.onclick=()=>choose(c3);

document.addEventListener("mousemove",(e)=>{

let x=e.clientX;

bird.style.left=x+"px";
paper.style.left=x+"px";

});

document.addEventListener("touchmove",(e)=>{

let x=e.touches[0].clientX;

bird.style.left=x+"px";
paper.style.left=x+"px";

});

function finishLevel(){

const msgs=[
"🎉 Tahniah!",
"🌟 Anda Hebat!",
"👏 Syabas!",
"🚀 Bravo!",
"💯 Khalas!"
];

message.innerHTML=
msgs[Math.floor(Math.random()*msgs.length)];

endScreen.style.display="flex";
}

function restartGame(){

round=1;
endScreen.style.display="none";
newRound();

}

function nextLevel(){

if(level<10){

level++;

game.className=
"level"+level;

round=1;

endScreen.style.display="none";

newRound();

}
else{

alert("Anda telah menamatkan semua 10 level!");

}

}

noteBtn.onclick=()=>{
note.style.display="block";
}

</script>

</body>
</html>
