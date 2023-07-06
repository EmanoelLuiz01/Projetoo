<style>
    .background {
      background-image: url("https://png.pngtree.com/png-vector/20220818/ourlarge/pngtree-sports-stadium-with-soccer-goal-vector-illustration-png-image_5890244.png");
      background-size: cover;
      background-position: center;
      height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
    }
  
    .grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      grid-gap: 10px;
    }
  
      .transparent-button {
        background-color: transparent;
        border: 2px solid green;
        color: green;
        padding: 10px;
        cursor: pointer;
			  width: 190px;
        height: 110px;
        font-size: 16px;
    }
  </style>
  
  <script>
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
    ];
  
    let pontos = 0;
    let tentativas = 5;
  
    function shoot() {
      const result = Math.random() < 0.5; // Simula o chute do jogador
  
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
        <button on:click={reiniciarJogo}>Tente denovo</button>
      {/if}
    </div>
  </main>
  
