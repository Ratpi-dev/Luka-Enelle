<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Luka ❤️ Enelle</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial,sans-serif;
}

body{
    background:linear-gradient(135deg,#ffd6e8,#ffc3d6);
    min-height:100vh;
    overflow:hidden;
    position:relative;
}

/* ===== QUIZ ===== */

.quiz-screen{
    position:fixed;
    inset:0;
    display:flex;
    justify-content:center;
    align-items:center;
    padding:20px;
    z-index:1000;
}

.quiz-card{
    width:min(92%,650px);
    background:rgba(255,255,255,.9);
    backdrop-filter:blur(10px);
    padding:35px;
    border-radius:25px;
    text-align:center;
    box-shadow:0 20px 40px rgba(0,0,0,.15);
    z-index:10;
}

.quiz-card h2{
    color:#ff4d88;
    margin-bottom:20px;
}

.quiz-card p{
    margin:15px 0;
    color:#333;
    line-height:1.6;
}

.small{
    font-size:.85rem;
    color:#777;
}

input[type="text"]{
    width:100%;
    padding:14px;
    border-radius:15px;
    border:2px solid #ffd1e1;
    outline:none;
    font-size:1rem;
    margin-top:15px;
}

.options{
    text-align:left;
    margin-top:20px;
}

.options label{
    display:block;
    background:white;
    padding:12px;
    border-radius:12px;
    margin:10px 0;
    cursor:pointer;
}

button{
    background:#ff4d88;
    color:white;
    border:none;
    padding:15px 30px;
    border-radius:50px;
    font-size:1rem;
    cursor:pointer;
    margin-top:20px;
}

button:hover{
    transform:scale(1.05);
}

.result{
    margin-top:20px;
    font-weight:bold;
    min-height:30px;
}

.shake{
    animation:shake .4s;
}

@keyframes shake{
    0%{transform:translateX(0);}
    25%{transform:translateX(-8px);}
    50%{transform:translateX(8px);}
    75%{transform:translateX(-8px);}
    100%{transform:translateX(0);}
}

/* ===== PAGE PRINCIPALE ===== */

#mainSite{
    display:none;
}

h1{
    color:#ff4d88;
    margin-bottom:10px;
    font-size:2rem;
    white-space:nowrap;
    display:flex;
    justify-content:center;
    align-items:center;
    gap:6px;
}

.card{
    position:relative;
    z-index:10;
    width:min(90%,700px);
    margin:100px auto;
    background:rgba(255,255,255,.88);
    backdrop-filter:blur(10px);
    padding:30px;
    border-radius:25px;
    text-align:center;
    box-shadow:0 20px 40px rgba(0,0,0,.15);
}

.quote{
    font-size:1.2rem;
    line-height:1.6;
    margin-bottom:25px;
    color:#333;
}

.counter{
    font-size:1rem;
    margin-bottom:25px;
    line-height:1.8;
}

.secret{
    display:none;
    margin-top:25px;
    background:#fff;
    padding:20px;
    border-radius:15px;
    line-height:1.8;
}

/* ===== COEURS ===== */

.heart{
    position:fixed;
    top:-50px;
    pointer-events:none;
    z-index:1;
    animation:fall linear forwards;
    opacity:.9;
}

@keyframes fall{
    from{
        transform:translateY(-100px);
        opacity:1;
    }
    to{
        transform:translateY(110vh);
        opacity:0;
    }
}

@media(max-width:768px){
    .card{
        width:92%;
        margin-top:100px;
        padding:25px;
    }

    h1{
        font-size:1.6rem;
    }
}
</style>
</head>

<body>

<!-- QUESTION 1 -->
<div class="quiz-screen" id="quiz1">
    <div class="quiz-card" id="card1">
        <h2>💜 Question 1 💜</h2>

        <p><b>Le jour où on s'est rencontré</b></p>

        <input type="text" id="answer1" placeholder="Écris la date...">

        <div class="result" id="result1"></div>

        <button onclick="checkQuestion1()">
            Valider ❤️
        </button>
    </div>
</div>

<!-- QUESTION 2 -->
<div class="quiz-screen" id="quiz2" style="display:none;">
    <div class="quiz-card" id="card2">
        <h2>💙 Question 2 💙</h2>

        <p><b>Le jour où on a officialisé</b></p>

        <input type="text" id="answer2" placeholder="Écris la date...">

        <div class="result" id="result2"></div>

        <button onclick="checkQuestion2()">
            Valider ❤️
        </button>
    </div>
</div>

<!-- QUESTION 3 -->
<div class="quiz-screen" id="quiz3" style="display:none;">
    <div class="quiz-card" id="card3">

        <h2>💛 Question 3 💛</h2>

        <p><b>Ce qui m'a fait tomber amoureux de toi</b></p>

        <p class="small">
            Plusieurs réponses sont attendues 💕
        </p>

        <div class="options">

            <label>
                <input type="checkbox" value="1">
                Ton sourire
            </label>

            <label>
                <input type="checkbox" value="2">
                Tes yeux
            </label>

            <label>
                <input type="checkbox" value="3">
                Ton rire
            </label>

            <label>
                <input type="checkbox" value="4">
                Ton corps
            </label>

            <label>
                <input type="checkbox" value="5">
                Ton visage
            </label>

            <label>
                <input type="checkbox" value="6">
                Ta personnalité
            </label>

        </div>

        <div class="result" id="result3"></div>

        <button onclick="checkQuestion3()">
            Valider ❤️
        </button>

    </div>
</div>

<!-- PAGE PRINCIPALE -->
<div id="mainSite">

    <div class="card">

        <h1><span>❤️</span> Luka & Enelle <span>❤️</span></h1>

        <p class="quote">
            « Pour celle qui a su faire sourire l'enfant qui est en moi »
        </p>

        <div class="counter" id="counter"></div>

        <button onclick="showSecret(event)">
            💌 Clique ici mon amour
        </button>

        <div class="secret" id="secret"></div>

    </div>

</div>

<script>

/* ===========================
   VARIABLES QUIZ
=========================== */

let tries1 = 0;
let tries2 = 0;
let tries3 = 0;

/* ===========================
   DATES ACCEPTÉES
=========================== */

const dateRencontre = [
    "6 juin 2025",
    "06 juin 2025",
    "6/6/2025",
    "06/06/2025",
    "6-6-2025",
    "06-06-2025",
    "06.06.2025",
    "6.6.2025",
    "06062025",
    "6 juin",
    "06 juin"
];

const dateOfficialisation = [
    "4 juillet 2025",
    "04 juillet 2025",
    "4/7/2025",
    "04/07/2025",
    "4-7-2025",
    "04-07-2025",
    "04.07.2025",
    "4.7.2025",
    "04072025",
    "4 juillet",
    "04 juillet"
];

/* ===========================
   FONCTION MESSAGE
=========================== */

function showMessage(element, text, color){
    element.innerHTML = text;
    element.style.color = color;
}

function shake(card){
    card.classList.remove("shake");
    void card.offsetWidth;
    card.classList.add("shake");
}

function wrongAnswer(result, card, tries){
    shake(card);

    if(tries >= 3){
        showMessage(
            result,
            "📞 si ta besoin d’un indice appelle moi 😘",
            "#ff4d88"
        );
    }else{
        showMessage(
            result,
            "❌ faux essaye encore 😡",
            "#e53935"
        );
    }
}

/* ===========================
   QUESTION 1
=========================== */

function checkQuestion1(){

    const value = document
        .getElementById("answer1")
        .value
        .trim()
        .toLowerCase();

    const result = document.getElementById("result1");
    const card = document.getElementById("card1");

    if(dateRencontre.includes(value)){

        showMessage(
            result,
            "🥳 Bien joué mon cœur 🥳🥳🫶🏼🫶🏼",
            "#22aa55"
        );

        setTimeout(()=>{
            document.getElementById("quiz1").style.display="none";
            document.getElementById("quiz2").style.display="flex";
            heartColor = "💙";
        },1500);

    }else{
        tries1++;
        wrongAnswer(result,card,tries1);
    }
}

/* ===========================
   QUESTION 2
=========================== */

function checkQuestion2(){

    const value = document
        .getElementById("answer2")
        .value
        .trim()
        .toLowerCase();

    const result = document.getElementById("result2");
    const card = document.getElementById("card2");

    if(dateOfficialisation.includes(value)){

        showMessage(
            result,
            "🥳 Bien joué mon cœur 🥳🥳🫶🏼🫶🏼",
            "#22aa55"
        );

        setTimeout(()=>{
            document.getElementById("quiz2").style.display="none";
            document.getElementById("quiz3").style.display="flex";
            heartColor = "💛";
        },1500);

    }else{
        tries2++;
        wrongAnswer(result,card,tries2);
    }
}

/* ===========================
   QUESTION 3
=========================== */

function checkQuestion3(){

    const checked =
        document.querySelectorAll(
            '#quiz3 input[type="checkbox"]:checked'
        );

    const result = document.getElementById("result3");
    const card = document.getElementById("card3");

    if(checked.length === 6){

        showMessage(
            result,
            "🥳 Bien joué mon cœur 🥳🥳🫶🏼🫶🏼",
            "#22aa55"
        );

        setTimeout(()=>{
            document.getElementById("quiz3").style.display="none";
            document.getElementById("mainSite").style.display="block";
            heartColor = "❤️";
            document.body.style.overflow = "auto";
        },1500);

    }else{
        tries3++;
        wrongAnswer(result,card,tries3);
    }
}

/* ===========================
   MESSAGE SECRET
=========================== */

const messageSecret = `
Merci d'être entrée dans ma vie ❤️

Merci pour tous les sourires,
les fous rires,
les moments passés ensemble.

Cette première année avec toi
a été l'une des plus belles de ma vie.

❤️ Je t'aime ❤️
`;

function showSecret(event){

    const secret =
        document.getElementById("secret");

    secret.style.display = "block";

    secret.innerHTML =
        messageSecret.replace(/\n/g,"<br>");

    event.target.disabled = true;

    event.target.innerText =
        "💌 Message ouvert ❤️";
}

/* ===========================
   COMPTEUR D'AMOUR
=========================== */

const startDate = new Date("2025-07-04T00:00:00");

function updateCounter(){

    const now = new Date();
    const diff = now - startDate;

    const totalSeconds = Math.floor(diff / 1000);

    const days = Math.floor(totalSeconds / (60*60*24));
    const hours = Math.floor((totalSeconds / (60*60)) % 24);
    const minutes = Math.floor((totalSeconds / 60) % 60);
    const seconds = totalSeconds % 60;

    const counter = document.getElementById("counter");

    if(counter){
        counter.innerHTML = `
        ❤️ <b>${days}</b> jour(s)<br>
        ⏰ <b>${hours}</b> heure(s)<br>
        💕 <b>${minutes}</b> minute(s)<br>
        ✨ <b>${seconds}</b> seconde(s)
        `;
    }
}

updateCounter();
setInterval(updateCounter,1000);

/* ===========================
   PLUIE DE COEURS
=========================== */

let heartColor = "💜";

function createHeart(){

    const heart = document.createElement("span");
    heart.className = "heart";
    heart.textContent = heartColor;

    heart.style.left = Math.random() * 100 + "vw";
    heart.style.fontSize = (Math.random() * 35 + 20) + "px";
    heart.style.animationDuration = (Math.random() * 5 + 5) + "s";

    document.body.appendChild(heart);

    heart.addEventListener("animationend", () => {
        heart.remove();
    });
}

setInterval(createHeart, 50);

document.body.style.overflow = "hidden";
