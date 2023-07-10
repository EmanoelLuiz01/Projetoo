<script>
    import { trocarEstadoDoJogo } from './Estado.js';

    console.log('teste');
</script>

<main>
    <div class="background">
        <div class="container">
            <h1 style="font-family: 'YourFont', sans-serif; color: white;">Score hero</h1>
            <button on:click={() => {trocarEstadoDoJogo("jogar"); }} class="jogar">Jogar</button>
        </div>
        <div class="container">
            <button on:click={() => trocarEstadoDoJogo("sobre")}>Sobre</button>
        </div>
    </div>
</main>

<style>

    .container {
        text-align: center;
    }

    .jogar {
        margin-bottom: 10px;
    }
</style>
