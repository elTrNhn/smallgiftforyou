# smallgiftforyou
<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Quà 8/3 cho bé</title>

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family: "Segoe UI", sans-serif;
}

body{
height:100vh;
background: linear-gradient(135deg,#ffd9ec,#e3f6ff);
display:flex;
align-items:center;
justify-content:center;
overflow:hidden;
}

/* CARD */

.card{
width:90%;
max-width:500px;
height:300px;
position:relative;
perspective:1000px;
}

.card-inner{
position:absolute;
width:100%;
height:100%;
transition:1s;
transform-style:preserve-3d;
}

.card.open .card-inner{
transform:rotateY(180deg);
}

.card-front, .card-back{
position:absolute;
width:100%;
height:100%;
border-radius:20px;
backface-visibility:hidden;
display:flex;
align-items:center;
justify-content:center;
flex-direction:column;
padding:30px;
box-shadow:0 10px 25px rgba(0,0,0,0.2);
}

.card-front{
background:white;
}

.card-back{
background:#fff0f6;
transform:rotateY(180deg);
text-align:center;
}

h1{
color:#ff4f81;
margin-bottom:10px;
}

p{
font-size:18px;
line-height:1.6;
color:#444;
}

button{
margin-top:20px;
padding:12px 25px;
border:none;
border-radius:25px;
background:#ff6fa5;
color:white;
font-size:16px;
cursor:pointer;
}

/* FLOWER */

.flower{
position:fixed;
top:-10px;
font-size:20px;
animation:fall linear infinite;
}

@keyframes fall{
to{
transform:translateY(110vh);
}
}

/* HEART */

.heart{
position:fixed;
color:red;
font-size:18px;
pointer-events:none;
animation:float 1s ease-out;
}

@keyframes float{
to{
transform:translateY(-40px);
opacity:0;
}

}

/* MOBILE */

@media (max-width:500px){

.card{
height:350px;
}

p{
font-size:16px;
}

}

</style>
</head>

<body>

<div class="card" id="card">

<div class="card-inner">

<div class="card-front">
<h1>💌 Gửi bé yêu</h1>
<p>Anh có một món quà nhỏ...</p>
<button onclick="openCard()">Mở thiệp</button>
</div>

<div class="card-back">

<h1>Happy 8/3 💖</h1>

<p id="daysText"></p>

<p>
Chúc bé yêu 8/3 vui vẻ, cảm ơn em đã đến bên anh và yêu anh trong
<b id="days"></b> ngày qua.  
Tình cảm này với anh giống như một món quà vô giá mà anh không tài nào đền đáp nổi.  
Chỉ mong rằng sau này anh vẫn luôn có thể ở bên cạnh em, cùng em đi qua thật nhiều ngày tháng nữa và làm cho em cười nhiều hơn mỗi ngày. 💗
</p>

</div>

</div>

</div>

<script>

/* OPEN CARD */

function openCard(){
document.getElementById("card").classList.add("open")
}

/* LOVE DAYS */

const startDate = new Date("2024-02-29")
const today = new Date()

const diff = today - startDate

const days = Math.floor(diff/(1000*60*60*24))

document.getElementById("days").innerText = days
document.getElementById("daysText").innerText =
"Chúng ta đã bên nhau được " + days + " ngày rồi đó 💞"

/* FLOWER FALL */

function createFlower(){

const flower=document.createElement("div")
flower.innerHTML="🌸"
flower.className="flower"

flower.style.left=Math.random()*100+"vw"
flower.style.animationDuration=(5+Math.random()*5)+"s"
flower.style.fontSize=(15+Math.random()*20)+"px"

document.body.appendChild(flower)

setTimeout(()=>flower.remove(),10000)

}

setInterval(createFlower,400)

/* HEART FOLLOW MOUSE */

document.addEventListener("mousemove",function(e){

const heart=document.createElement("div")
heart.innerHTML="❤"
heart.className="heart"

heart.style.left=e.clientX+"px"
heart.style.top=e.clientY+"px"

document.body.appendChild(heart)

setTimeout(()=>heart.remove(),1000)

})

/* MOBILE TOUCH HEART */

document.addEventListener("touchmove",function(e){

const touch=e.touches[0]

const heart=document.createElement("div")
heart.innerHTML="❤"
heart.className="heart"

heart.style.left=touch.clientX+"px"
heart.style.top=touch.clientY+"px"

document.body.appendChild(heart)

setTimeout(()=>heart.remove(),1000)

})

</script>

</body>
</html>
