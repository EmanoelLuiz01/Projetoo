  <script>
    import { onMount } from 'svelte';
    import { trocarEstadoDoJogo } from "./Estado";
    import Menu from "./Menu.svelte";
    import Voltarmenu from "./voltarmenu.svelte";
    const audio = new Audio('https://65381g.ha.azioncdn.net/f/3/0/a/mobiloes-bomba-patch-f3607330.mp3');
    
    let src = ``

    let goalkeepDirection = " "

    let canShoot = true

    let result = 'Aguardando chute!'

    onMount(async () => {
      console.log('on mount');
      audio.play();
    });

    function reproduzirMusica() {
      console.log('play');
      audio.play(); 
    }

    function pausarMusica() {
      console.log('pause');
      audio.pause(0);
    }
    //reproduzirMusica();
   
    let pontos = 0;
    let tentativas = 5;
    
    
    function shoot(p) {
      canShoot = false

      let shootPosition = p

      let goalKeep = Math.floor(Math.random() * 3) // Simula o chute do jogador
      
      
      if (shootPosition != goalKeep) {
        pontos += 1
        result = "Gooooooooool!"
        src = "images/gol.gif"
        goalkeepDirection = "gol"
        
        
      } else {
       if (shootPosition == 0 && goalKeep == 0) {
          src = "images/goalkeep-left.gif"
          goalkeepDirection = "goalkeep-left"
        } else if (shootPosition == 1 && goalKeep == 1) {
          src = " images/goalkeep-centro.gif"
          goalkeepDirection = " goalkeep-centro"
        } else {
          src = "images/goalkeep-right.gif"
          goalkeepDirection = "goalkeep-rigth"
        }
      }
     
      tentativas -= 1;
      if (tentativas === 0) {
        alert("Fim de jogo. Pontuação final: " + pontos);
      }

      

      setTimeout(() => {
        alert("Clique OK para ir para o próximo chute!")

        canShoot = true
        src = " " 
        goalkeepDirection = " "
        result = "Aguardando chute!"
      }, 1000)
     
    }
    
      
    function reiniciarJogo() {
      pontos = 0;
      tentativas = 5;   
    }
    
  </script>
  
  <main class="container">
    <h1>{ result }</h1>
    <h5>Gols: { pontos } | Defesas: { 5 - [ pontos + tentativas ] } | Chances restantes: { tentativas }</h5>
    <div class="goal">
      {#if tentativas > 0}
        <div class="grid">
          <button class="posicao-0" on:click={() => canShoot === true ? shoot(0) : ''}> </button>
          <button class="posicao-1" on:click={() => canShoot === true ? shoot(1) : ''}> </button>
          <button class="posicao-2" on:click={() => canShoot === true ? shoot(2) : ''}> </button>
          <div class={ goalkeepDirection }>
            <img { src } class="goalkeep-img">
          </div>
        </div>
      {:else}
        <button on:click={reiniciarJogo}>Tente de novo</button>
        <button on:click={() => {
          trocarEstadoDoJogo("menu");
          pausarMusica();
          }
        }>Voltar ao menu</button>
     {/if}
     
    </div>
  </main>
  
  <style>
    
    .container {
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
    }

    .goal {
      height: 70%;
      width: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .grid {
      height: 100%;
      width: 100%;
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      position: relative;
    }
    
    .goalkeep-rigth {
      height: 100%;
      width: 100%;
      position: absolute;
      display: flex;
      justify-content: end;
    }

    .goalkeep-left {
      height: 100%;
      width: 100%;
      position: absolute;
      display: flex;
      justify-content: start;
    }
    .goalkeep-centro {
      height: 100%;
      width: 100%;
      position: absolute;
      display: flex;
      justify-content: space-around;
    
    }
    .goalkeep-img {
      width: 60%;
    }
    .gol {
      height: 100%;
      width: 80%;
      position: absolute;
      display: flex;
      justify-content: space-around;
    }

    .posicao-0 {
      grid-column-start: 1;
      grid-column-end: 2;
      border-top: 5px solid black;
      border-left: 5px solid black;
      border-right: none;
      border-bottom: none;
      height: 100%;
    }

    .posicao-1 {
      grid-column-start: 2;
      grid-column-end: 3;
      border-top: 5px solid black;
      border-left: none;
      border-right: none;
      border-bottom: none;
      height: 100%;
    }

    .posicao-2 {
      grid-column-start: 3;
      border-top: 5px solid black;
      border-left: none;
      border-right: 5px solid black;
      border-bottom: none;
      height: 100%;
    }

    .posicao-0, .posicao-1, .posicao-2 {
      background-color: rgb(177, 177, 177);
      height: 100%;
      margin: 0;
      padding: 0;
    }
    
  
    
    

  </style>
  
