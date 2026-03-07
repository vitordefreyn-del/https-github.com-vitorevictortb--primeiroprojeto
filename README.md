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
