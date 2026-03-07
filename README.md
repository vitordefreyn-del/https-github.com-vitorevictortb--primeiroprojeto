# https-github.com-vitorevictortb--primeiroprojeto
 <!DOCTYPE html>
<html lang="pt">
<head>
<meta charset="UTF-8">
<title>Descubra a palavra Oculta</title>
<link rel="stylesheet" href="style.css">
<style>
body{
    font-family: ubuntu;
    text-align:center;
    color: black;
}

#forca{
    margin-top:20px;
}

#palavra{
    font-size:35px;
    letter-spacing:10px;
}

#letrasErradas{
    color:red;
    font-size:25px;
    font-weight:bold;
}

input{
    padding:5px;
    font-size:17px;
}

.button{
    font-size:16px;
    padding:5px 10px;
    cursor:pointer;
}
</style>
</head>

<body>
<h1 class="titulo">Descubra a palavra Oculta</h1>

<div id="forca">
    <pre id="boneco">
 (ദ്ദി˙ᗜ˙)
    </pre>
</div>

<h2 id="palavra"></h2>
<p>Dica: <span id="dica"></span></p>
<p>Letras Erradas: <span id="letrasErradas"></span></p>

<input type="text" id="letra" maxlength="1">
<button class="button" onclick="tentarLetra()">Tentar</button>
<button class="button" onclick="mostrarDica()">Mostrar Dica</button>

<script>
const palavras = [
"banana","morango","abacaxi","laranja","uva",
"flamengo","palmeiras","barcelona","chelsea"
];

const dicas = [
  "Fruta amarela e doce",        // banana
  "Fruta vermelha muito doce",   // morango
  "Fruta tropical com casca dura", // abacaxi
  "Fruta cítrica laranja",       // laranja
  "Fruta pequena e roxa",        // uva
  "Time de futebol carioca",    // flamengo
  "Time paulista famoso",        // palmeiras
  "Time espanhol famoso",        // barcelona
  "Time inglês da Premier League" // chelsea
];

// Sorteia palavra e dica
let indice = Math.floor(Math.random() * palavras.length);
let palavra = palavras[indice];
let dica = dicas[indice];

// Inicializa o jogo
let palavraOculta = [];
let letrasErradas = [];
let erros = 0;

for(let i=0;i<palavra.length;i++){
    palavraOculta.push("_");
}

document.getElementById("palavra").innerText = palavraOculta.join(" ");
document.getElementById("dica").style.display = "none"; // dica escondida no início

function mostrarDica() {
    document.getElementById("dica").innerText = dica;
    document.getElementById("dica").style.display = "inline";
}

const estagios = [
` ( ˶ˆᗜˆ˵ ) `,
` (˶º⤙º˶) `,
` ( ¬_¬ ) `,
` ˚‧º·(˚ ˃̣̣̥⌓˂̣̣̥ )‧º·˚ `,
` (ﾉ｀□´)ﾉ⌒┻━┻ `,
` (╥﹏╥) `,
` ̿̿ ̿̿ ̿̿ ̿’̿’\\̵͇̿̿\\з= ( ▀ ͜͞ʖ▀) =ε/̵͇̿̿/’̿’̿ ̿ ̿̿ ̿̿ `
];

function tentarLetra(){
    let input = document.getElementById("letra");
    let letra = input.value.toLowerCase();
    input.value="";

    if(!letra) return;

    if(palavra.includes(letra)){
        for(let i=0;i<palavra.length;i++){
            if(palavra[i]===letra){
                palavraOculta[i]=letra;
            }
        }
    } else {
        if(!letrasErradas.includes(letra)){
            letrasErradas.push(letra);
            erros++;
        }
    }

    document.getElementById("palavra").innerText = palavraOculta.join(" ");
    document.getElementById("letrasErradas").innerText = letrasErradas.join(", ");
    document.getElementById("boneco").innerText = estagios[erros];

    if(!palavraOculta.includes("_")){
        alert("🎉 Você venceu!");
        location.reload();
    }

    if(erros===6){
        alert("💀 Você perdeu! Palavra: "+palavra);
        location.reload();
    }
}
</script>
</body>
</html>
html{
box-sizing:border-box;
-ms-text-size-adjust:100%;
-webkit-text-size-adjust:100%;
overflow-x:hidden;
}
body{
    background-color: rgb(121, 31, 31);
    box-shadow: inset 0 0 50px rgba(0, 0, 0, 0.1);
    
}
*,*:before,*:after{
box-sizing:inherit;
}

body{
margin:0;
font-family: ubuntu ;
font-size:16px;
line-height:100%;
text-shadow:1px 1px 3px ;
}

/* BARRAS AMARELAS */

#TOP{
position:fixed;
background-color:yellow;
width:100%;
height:5%;
top:0;
}

#LEFT{
position:fixed;
background-color:yellow;
width:7.5%;
height:100%;
left:0;
}

#RIGHT{
position:fixed;
background-color:yellow;
width:7.5%;
height:100%;
right:0;
}

#MEIO{
position:fixed;
background-color:yellow;
width:100%;
height:7%;
top:55%;
}

#BOTTOM{
position:fixed;
background-color:yellow;
width:100%;
height:5%;
bottom:0;
}

/* TÍTULO */

#X01{
display:block;
position:relative;
top:15%;
line-height:10%;
color:#3a3737;
text-shadow:0 4px 8px #000;
text-align:center;
font-size:130%;
}

/* AVISOS */

#h01{
display:none;
letter-spacing:2px;
text-shadow:0 4px 8px #888;
text-align:center;
font-size:130%;
color:#F00;
position:absolute;
top:50%;
transform:rotate(-35deg);
}

#h02{
display:block;
position:absolute;
text-shadow:0 4px 8px #000000;
font-size:80%;
right:5px;
top:5px;
}

#letrasErradas{
left:0.5%;
font-size:200%;
font-weight: bold;
 color:rgb(209, 47, 6) ;
 text-shadow:0 0 5px black ;
}

/* RODAPÉ */

#rdp{
position:relative;
text-align:center;
bottom:5%;
font-size:80%;
}

/* AREA DO JOGO */

#DIVCORPO{
position:fixed;
width:85%;
height:50%;
right:7.5%;
top:5%;
padding:15px 0 0 15px;
border:1px ridge black;
border-radius:8px;
}
#DIVCORPO:hover {
    background-color: rgb(180, 60, 60);
    box-shadow: 0 10px 25px rgba(0,0,0,0.5); 
    transition: 0.3s; 
}

/* FORCA */

#forca{
margin-top:20px;
background:rgb(158, 44, 44);
padding:20px;
border-radius:10px;
display:inline-block;
box-shadow: 0 0 10px rgba(0,0,0,0.4);
}

/* CABEÇA */

#CABECA{
display:none;
width:25.6px;
height:26.4px;
background:#FFCCCC;
position:absolute;
left:70px;
top:30px;
border-radius:25px;
}

#ROSTO{
display:none;
line-height:24px;
font-size:12px;
text-shadow:0 0 1px #F00;
position:relative;
top:-16px;
}

#CHAPEU{
display:none;
width:19.2px;
height:12.8px;
background:black;
position:absolute;
left:73.4px;
top:22px;
border-radius:12px;
}

#ABA{
display:none;
width:32px;
height:3.2px;
background:black;
position:relative;
border-radius:12px;
}

#PESCOCO{
display:none;
width:11.2px;
height:8px;
background:#FFCCCC;
position:absolute;
left:7px;
top:26px;
border-radius:2px;
}

/* TRONCO */

#TRONCO{
display:none;
width:32px;
height:48px;
background:blue;
position:absolute;
left:66.5px;
top:57px;
border-radius:50% / 40% 40% 8% 8%;
}

/* FORMULÁRIOS */

input[type=text]{
font-size:1em;
margin:1px;
border:2.5px solid #DDD;
border-radius:4px;
text-align:center;
}

input[type=radio]{
width:5%;
}

form.style1 label{
float:left;
margin-right:0.5em;
padding-top:0.2em;
text-align:right;
font-weight:bold;
}

/* BOTÃO */

.button {
  display: inline-block;
  font-size: 18px;
  font-weight: bold;
  cursor: pointer;
  text-align: center;
  color: rgb(146, 83, 83);
  background: rgb(114, 11, 11);
  border: none;
  border-radius: 6px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.5);
  transition: 0.3s;
}

.button:hover {
  background-color: rgb(161, 67, 39);
  color: rgb(29, 11, 11); /* muda a cor do texto também */
  box-shadow: 0 6px 12px rgba(0,0,0,0.5);
}
.button:active {
  background-color: #9c1616;
  box-shadow: 0 2px 4px rgba(165, 27, 27, 0.4);
  transform: translateY(1.5px);
}

#TOP, #LEFT, #RIGHT, #BOTTOM {
  box-shadow: 0 0 10px rgba(0,0,0,0.4);
}
#MEIO {
  box-shadow: inset 0 0 50px rgba(0,0,0,0.2);
}







