<style>
    .background {
      background-image: url("https://png.pngtree.com/png-vector/20220818/ourlarge/pngtree-sports-stadium-with-soccer-goal-vector-illustration-png-image_5890244.png");
      background-size: cover;
      background-position: center;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding-top:115px;
    }

    .grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      grid-gap: 0px;
    }
  
      .transparent-button {
        background-color: transparent;
        border: 1px solid transparent;
        color: green;
        padding: 10px;
        cursor: pointer;
			  width: 325px;
        height: 148px;
        font-size: 0px;
    }
    
  </style>
  
  <script>
    import { onMount } from 'svelte';
    import { trocarEstadoDoJogo } from "./Estado";
    import Menu from "./Menu.svelte";
    import Voltarmenu from "./voltarmenu.svelte";
    const audio = new Audio('https://65381g.ha.azioncdn.net/f/3/0/a/mobiloes-bomba-patch-f3607330.mp3');

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
    let buttons = [
      {
        text: ''
      },
      {
        text: ''
      },
      {
        text: ''
      },
      {
        text: ''
      },
      {
        text: ''
      },
      {
        text: ''
      },
      {
        text: ''
      },
      {
        text: ''
      },
      {
        text: ''
      },
      {
        text: ''
      },
      {
        text: ''
      },{
        text: ''
      },
    ];
  
    let pontos = 0;
    let tentativas = 5;
  
    function shoot() {
      const result = Math.random() < 0.1; // Simula o chute do jogador
  
      if (result) {
        pontos += 1;
        alert("Gol!");
      } else {
        alert("Defendido!");
      }
  
      tentativas -= 1;
  
      if (tentativas === 0) {
        alert("Fim de jogo. Pontuação final: " + pontos);
        buttons = []; // Remover os botões restantes
      }
    }
  
    function reiniciarJogo() {
      pontos = 0;
      tentativas = 5;
      buttons = [
        {
        text: ''
      },
      {
        text: ''
      },
      {
        text: ''
      },
      {
        text: ''
      },
      {
        text: ''
      },
      {
        text: ''
      },
      {
        text: ''
      },
      {
        text: ''
      },
      {
        text: ''
      },
      {
        text: ''
      },
      {
        text: ''
      },{
        text: ''
      },
      ]; // Restaurar os botões
    }
    
  </script>
  
  <main>
    <div class="background">
      {#if tentativas > 0}
        <div class="grid">
          {#each buttons as button}
            <button class="transparent-button" on:click={shoot}>{button.text}</button>
          {/each}
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
  
