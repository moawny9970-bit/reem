<!DOCTYPE html>
<html lang="ar">
<head>
<meta charset="UTF-8">
<title>Love Letter</title>

<style>

body{
margin:0;
font-family:'Segoe UI';
background:black;
overflow:hidden;
color:white;
}

/* شاشة دخول سينمائي */

#intro{
position:absolute;
width:100%;
height:100%;
background:black;
display:flex;
justify-content:center;
align-items:center;
font-size:35px;
letter-spacing:3px;
animation:fadeOut 3s forwards;
animation-delay:2s;
}

@keyframes fadeOut{
to{
opacity:0;
visibility:hidden;
}
}

/* دباديب */

body::before{
content:"🧸 🧸 🧸 🧸 🧸";
position:fixed;
font-size:60px;
opacity:0.08;
width:100%;
text-align:center;
top:30%;
}

/* صفحة الباسورد */

#loginPage{
position:absolute;
width:100%;
height:100%;
display:flex;
justify-content:center;
align-items:center;
flex-direction:column;
background:linear-gradient(135deg,#ff758c,#ff7eb3);
}

input{
padding:12px;
border-radius:25px;
border:none;
font-size:18px;
text-align:center;
}

button{
margin-top:10px;
padding:10px 25px;
border:none;
border-radius:25px;
background:white;
color:#ff4b7d;
font-weight:bold;
cursor:pointer;
}

/* الصفحة الرئيسية */

#mainPage{
display:none;
position:absolute;
width:100%;
height:100%;
overflow:auto;
text-align:center;
padding:20px;
background:linear-gradient(135deg,#ff9a9e,#fad0c4);
}

/* صورة */

.photo-frame{
margin-top:20px;
width:200px;
height:200px;
border-radius:50%;
overflow:hidden;
margin:auto;
border:6px solid white;
box-shadow:0 0 25px rgba(0,0,0,0.4);
}

.photo-frame img{
width:100%;
height:100%;
object-fit:cover;
}

/* الرسالة */

.message-box{
margin-top:25px;
background:white;
padding:25px;
border-radius:20px;
width:90%;
max-width:600px;
margin:auto;
font-size:18px;
line-height:1.8;
color:black;
box-shadow:0 0 20px rgba(0,0,0,0.3);
}

/* الصفحة التانية */

#secondPage{
display:none;
position:absolute;
width:100%;
height:100%;
text-align:center;
padding-top:40px;
background:linear-gradient(135deg,#ff758c,#ff7eb3);
}

/* العداد */

#counter{
font-size:22px;
margin-top:15px;
}

/* القلب */

.big-heart{
font-size:120px;
animation:pulse 1.5s infinite;
cursor:pointer;
}

@keyframes pulse{
0%{transform:scale(1);}
50%{transform:scale(1.2);}
100%{transform:scale(1);}
}

/* قلوب طايرة */

.heart{
position:absolute;
color:white;
animation:float 6s linear infinite;
}

@keyframes float{
0%{
transform:translateY(100vh);
opacity:1;
}
100%{
transform:translateY(-10vh);
opacity:0;
}
}

</style>

</head>

<body>

<div id="intro">
A ❤️ R
</div>

<audio id="song" src="song.mp3"></audio>

<!-- صفحة الباسورد -->

<div id="loginPage">

<h2>ادخل الباسورد 💖</h2>

<input type="password" id="password">

<button onclick="checkPassword()">دخول</button>

</div>

<!-- الصفحة الرئيسية -->

<div id="mainPage">

<div class="photo-frame">
<img src="photo.jpg">
</div>

<div class="message-box">

<p id="text"></p>

</div>

<button id="nextBtn" onclick="goNext()" style="display:none">
التالي ❤️
</button>

</div>

<!-- الصفحة التانية -->

<div id="secondPage">

<h2>
هنفضل سوا طول العمر إن شاء الله 🤍
</h2>

<div id="counter">
0 يوم 0 ساعة 0 دقيقة 0 ثانية
</div>

<h2>
عملتلك الموقع ده علشان أصالحك  
وبحبك أووووي بجد ❤️
</h2>

<div class="big-heart" onclick="explodeHearts()">
❤️<br>
A ❤️ R
</div>

</div>

<script>

/* الباسورد */

function checkPassword(){

let pass=document.getElementById("password").value;

if(pass=="5/4"){

document.getElementById("loginPage").style.display="none";
document.getElementById("mainPage").style.display="block";

startTyping();

document.getElementById("song").play();

startHearts();

}

else{

alert("الباسورد غلط");

}

}

/* الرسالة */

let message=`دي بصراحة وجودك في حياتي ي ريمو تاني مخليني مبسوط بطريقة صعب أوصفها. 
حاسس إن رجوعنا لبعض كان من أحلى الحاجات اللي حصلتلي.

أنا مقدر جدًا ثقتك فيا.

وجودك حواليا بيخليني مبسوط.

وبجد أنا ممتن لوجودك في حياتي 🤍`;

let i=0;

function startTyping(){

if(i<message.length){

document.getElementById("text").innerHTML+=message.charAt(i);

i++;

setTimeout(startTyping,35);

}

else{

document.getElementById("nextBtn").style.display="inline-block";

}

}

/* الصفحة التانية */

function goNext(){

document.getElementById("mainPage").style.display="none";
document.getElementById("secondPage").style.display="block";

startCounter();

}

/* عداد وقت كامل */

function startCounter(){

let startDate=new Date("2024-02-20T00:00:00");

setInterval(()=>{

let now=new Date();

let diff=now-startDate;

let days=Math.floor(diff/(1000*60*60*24));

let hours=Math.floor((diff/(1000*60*60))%24);

let minutes=Math.floor((diff/(1000*60))%60);

let seconds=Math.floor((diff/1000)%60);

document.getElementById("counter").innerHTML=
days+" يوم "+
hours+" ساعة "+
minutes+" دقيقة "+
seconds+" ثانية";

},1000);

}

/* قلوب طايرة */

function startHearts(){

setInterval(()=>{

let heart=document.createElement("div");

heart.className="heart";

heart.innerHTML="❤️";

heart.style.left=Math.random()*100+"%";

heart.style.fontSize=(Math.random()*20+15)+"px";

document.body.appendChild(heart);

setTimeout(()=>{
heart.remove();
},6000);

},300);

}

/* قلوب بتنفجر */

function explodeHearts(){

for(let i=0;i<25;i++){

let heart=document.createElement("div");

heart.innerHTML="💖";

heart.style.position="absolute";

heart.style.left="50%";
heart.style.top="60%";

heart.style.fontSize="25px";

document.body.appendChild(heart);

let x=(Math.random()*400)-200;
let y=(Math.random()*400)-200;

heart.animate([
{transform:"translate(0,0)",opacity:1},
{transform:`translate(${x}px,${y}px)`,opacity:0}
],{
duration:1000
});

setTimeout(()=>{
heart.remove();
},1000);

}

}

</script>

</body>
</html>
