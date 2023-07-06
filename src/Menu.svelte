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
    .background {
        background-image: url("https://png.pngtree.com/thumb_back/fw800/background/20220512/pngtree-soccer-football-championship-vector-background-with-sports-ball-and-goals-image_1192381.jpg");
        background-size: cover;
        background-position: center;
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
