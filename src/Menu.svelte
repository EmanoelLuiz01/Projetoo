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
            <button on:click={() => {trocarEstadoDoJogo("sobre");}} class = "Sobre">Sobre</button>
        </div>
    </div>
</main>

<style>
    .background {
      background-image: url("https://img.quizur.com/f/img5c633775e6dd31.52777503.jpg?lastEdited=1550006143");
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
    

  
 .Sobre{
   
    color: black;
 }
    .jogar {  
        color: black;
    }
   
    
</style>
