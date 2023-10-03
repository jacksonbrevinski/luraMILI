<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Alura MIDI</title>

    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@500;600&display=swap" rel="stylesheet">

    <link rel="icon" type="image/png" href="images/bateria.png">
    <link rel="stylesheet" href="css/reset.css">
    <link rel="stylesheet" href="css/estilos.css">

</head>
<body>

    <h1>Alura Midi</h1>

    <section class="teclado">
        <button class="tecla tecla_pom">Pom</button>
        <button class="tecla tecla_clap">Clap</button>
        <button class="tecla tecla_tim">Tim</button>

        <button class="tecla tecla_puff">Puff</button>
        <button class="tecla tecla_splash">Splash</button>
        <button class="tecla tecla_toim">Toim</button>

        <button class="tecla tecla_psh">Psh</button>
        <button class="tecla tecla_tic">Tic</button>
        <button class="tecla tecla_tom">Tom</button>
    </section>

    <audio src="sounds/keyq.wav" id="som_tecla_pom"></audio>
    <audio src="sounds/keyw.wav" id="som_tecla_clap"></audio>
    <audio src="sounds/keye.wav" id="som_tecla_tim"></audio>
    <audio src="sounds/keya.wav" id="som_tecla_puff"></audio>
    <audio src="sounds/keys.wav" id="som_tecla_splash"></audio>
    <audio src="sounds/keyd.wav" id="som_tecla_toim"></audio>
    <audio src="sounds/keyz.wav" id="som_tecla_psh"></audio>
    <audio src="sounds/keyx.wav" id="som_tecla_tic"></audio>
    <audio src="sounds/keyc.wav" id="som_tecla_tom"></audio>

    <script src="main.js"></script>

</body>
</html>







:root {
  --cinza: #aaa;
  --vermelha: #e93d50;
  --vermelha-escura: #af303f;
  --branca: #fff;
  --luz: rgb(229, 255, 0);
}

body {
  align-items: center;
  background: linear-gradient(45deg, #a7cfdf 0%,#23538a 100%);
  display: flex;
  justify-content: center;
  flex-direction: column;
  font-family: 'Montserrat', sans-serif;
  min-height: 100vh;
}

h1 {
  color: var(--branca);
  margin-bottom: 20px;
  font-size: 2rem;
}

.teclado {
  background: linear-gradient(to bottom, #eeeeee 0%,#cccccc 100%);
  box-shadow: 6px 8px 0 6px #666, 10px 10px 10px #000;
  border-radius: 30px;
  display: grid;
  gap: 10px;
  grid-template-columns: repeat(3, 1fr);
  padding: 10px;
}

.tecla {
  background-color: var(--branca);
  border-radius: 30px;
  box-shadow: 3px 3px 0 var(--cinza);
  color: var(--vermelha);
  cursor: pointer;
  height: 120px;
  font-size: 1.75em;
  font-weight: bold;
  line-height: 120px;
  text-align: center;
  width: 120px;
}

.tecla.ativa,
.tecla:active {
  background-color: var(--vermelha);
  border: 4px solid  var(--vermelha);
  box-shadow: 3px 3px 0 var(--vermelha-escura) inset;
  color: var(--branca);
  outline: none;
}

.tecla.focus,
.tecla:focus {
  outline: none;
  box-shadow: 1px 1px 10px var(--luz);
}

.tecla.active:focus,
.tecla:active:focus {
  box-shadow: 3px 3px 0 var(--vermelha-escura) inset, 1px 1px 10px var(--luz);
}








function tocaSom (idElementoAudio) {
    document.querySelector(idElementoAudio).play();
}

const listaDeTeclas = document.querySelectorAll('.tecla');

//para
for (let contador = 0; contador < listaDeTeclas.length; contador++) {

    const tecla = listaDeTeclas[contador];
    const instrumento = tecla.classList[1];
    const idAudio = `#som_${instrumento}`; //template string

    tecla.onclick = function () {
        tocaSom(idAudio);
    }

}
