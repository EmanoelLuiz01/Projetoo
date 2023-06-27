
<h1>Jogo</h1>

<script>
	import { trocarEstadoDoJogo } from './Estado.js';
</script>

<main>
    <div class="background">
        <div class="container">
            <button on:click={() => trocarEstadoDoJogo("jogar")} class="jogar">Jogar</button>
        </div>
        <div class="container">
            <button on:click={() => trocarEstadoDoJogo("sobre")}>Sobre</button>
        </div>
    </div>
</main>

<style>
    .background {
        background-color: green;
        height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    .container {
        text-align: center;
    }

    .jogar {
        margin-bottom: 10px;
    }
</style>

