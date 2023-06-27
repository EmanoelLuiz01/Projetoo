<script>
    let pontos = 0;
    let attempts = 5;
  
    function shoot() {
      const result = Math.random() < 0.5; // Simula o chute do jogador
  
      if (result) {
        pontos += 1;
        alert("Gol!");
      } else {
        alert("Defendido!");
      }
  
      attempts -= 1;
  
      if (attempts === 0) {
        alert("Fim de jogo. Pontuação final: " + pontos);
      }
    }
  </script>
  
  <main>
    <h1>Jogo de Pênaltis</h1>
  
    {#if attempts > 0}
      <button on:click={shoot}>Chutar</button>
    {/if}

  </main>
