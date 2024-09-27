<script>
  import Header from "./Header.svelte";

  export let showComponent;
  export let showChallengePanel;
</script>

<div class="container">
  <div class="row">
    <div class="functions" on:click={() => showComponent("➕")}>
      <p class="signo">➕</p>
       <p>Sumar</p>
     </div>
     <div class="functions" on:click={() => showComponent("➖")}>
       <p class="signo">➖</p>
       <p>Restar</p>
     </div>
     <div class="functions" on:click={() => showComponent("✖")}>
       <p class="signo">✖️</p>
       <p>Multiplicar</p>
     </div>
     <div class="functions" on:click={() => showComponent("➗")}>
       <p class="signo">➗</p>
       <p>Dividir</p>
     </div>
     </div>
     <div class="button" on:click={showChallengePanel}> ⬅️ Voler Atras</div>
</div>

<style>
  .container {
    width: 100%;
    height: 60vh;
    display: grid;
    place-items: center;
    margin-top: 3em;
  }
  .row{
    display: grid;
    grid-template-columns: repeat(2,1fr);
    gap: 2em;
    margin-bottom: 1em;
  }
  .functions {
    background-color: rgb(33, 150, 43);
    border-radius: 5px;
    padding: 1em;
    box-shadow: 0 0 3px rgb(33, 150, 43);
    height: 130px;
    width: 130px;
    display: grid;
    place-items: center;
   
  }
  img {
    height: 100px;
    width: 100px;
  }
  p {
    margin: 0;
    color: #fff;
    font-size: 1em;
    font-weight: bold;
  }
  .signo{
    font-size:2.5em;
  }
  .button {
    width: 84%;
    padding: 1em;
    background-color: rgb(33, 150, 43);
    border-radius: 5px;
    font-weight: bold;
    font-size: 1em;
    margin: 0 auto;
  }
</style>
