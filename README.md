<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>For You 💜</title>

<style>

body{
    margin:0;
    height:100vh;
    display:flex;
    justify-content:center;
    align-items:center;
    font-family:Arial;
    background:linear-gradient(135deg,#5a0dad,#a64dff);
    overflow:hidden;
    color:white;
    animation:glow 6s ease-in-out infinite;
}

/* BACKGROUND GLOW */
@keyframes glow{
    0%{background:linear-gradient(135deg,#5a0dad,#a64dff);}
    50%{background:linear-gradient(135deg,#7a1fd1,#c77dff);}
    100%{background:linear-gradient(135deg,#5a0dad,#a64dff);}
}

/* BOX */
.container{
    text-align:center;
    background:rgba(255,255,255,0.1);
    padding:40px;
    border-radius:20px;
    backdrop-filter:blur(10px);
}

/* BUTTONS */
button{
    padding:12px 25px;
    font-size:18px;
    margin:10px;
    border:none;
    border-radius:10px;
    cursor:pointer;
}

#yesBtn{
    background:#ff66cc;
    color:white;
}

#noBtn{
    background:#999;
    color:white;
    cursor:not-allowed;
}

/* LOVE PAGE */
#lovePage{
    display:none;
    text-align:center;
    padding:40px;
    max-width:700px;
}

/* TYPEWRITER */
#text{
    font-size:20px;
    border-right:2px solid white;
    white-space:nowrap;
    overflow:hidden;
}

/* HEARTS */
.heart{
    position:absolute;
    bottom:-20px;
    color:#ff99ff;
    animation:floatUp 6s linear infinite;
}

@keyframes floatUp{
    0%{transform:translateY(0);}
    100%{transform:translateY(-110vh);}
}

/* FLOWERS */
.flower{
    position:absolute;
    font-size:30px;
    opacity:0.8;
    animation:floatUp 8s linear infinite;
}

/* LINK */
a{
    display:block;
    margin-top:25px;
    font-size:18px;
    color:#ffccff;
}

</style>
</head>

<body>

<div class="container" id="mainPage">
    <h1>💜 can i try to lighten up your mood? 💜</h1>

    <button id="yesBtn">YES</button>
    <button id="noBtn">NO</button>
</div>

<div id="lovePage">
    <h1>❤️</h1>
    <p id="text"></p>

    <a href="https://www.youtube.com/watch?v=C7b9uheTzSk" target="_blank">
        🎶 listen to this song
    </a>
</div>

<script>

const yesBtn = document.getElementById("yesBtn");
const noBtn = document.getElementById("noBtn");
const mainPage = document.getElementById("mainPage");
const lovePage = document.getElementById("lovePage");
const textElement = document.getElementById("text");

/* DISABLE NO BUTTON */
noBtn.addEventListener("click", (e)=>{
    e.preventDefault();
});

/* TYPEWRITER */
const message = "I love you so much, and whenever you stress so do I, so I want to ask you to accept my offer and let me love you the most that I can, because you are the only person who deserves the full love I can give you.";

let i = 0;

function typeWriter(){
    if(i < message.length){
        textElement.innerHTML += message.charAt(i);
        i++;
        setTimeout(typeWriter, 35);
    }
}

/* YES CLICK */
yesBtn.onclick = () => {
    mainPage.style.display = "none";
    lovePage.style.display = "block";

    typeWriter();
    createHearts();
    createFlowers();
};

/* HEARTS */
function createHearts(){
    setInterval(()=>{
        let heart = document.createElement("div");
        heart.className = "heart";
        heart.innerHTML = "💜";

        heart.style.left = Math.random() * 100 + "vw";
        heart.style.fontSize = (Math.random()*20 + 15) + "px";

        document.body.appendChild(heart);

        setTimeout(()=>heart.remove(),6000);

    },300);
}

/* FLOWERS (Tulips + Orchids) */
function createFlowers(){
    const flowers = ["🌷","🌸"]; // tulips + orchids vibe

    setInterval(()=>{
        let f = document.createElement("div");
        f.className = "flower";
        f.innerHTML = flowers[Math.floor(Math.random()*flowers.length)];

        f.style.left = Math.random()*100 + "vw";
        f.style.fontSize = (Math.random()*20 + 25)+"px";

        document.body.appendChild(f);

        setTimeout(()=>f.remove(),8000);

    },500);
}

</script>

</body>
</html>
