<script>
  export let showComponent;
  export let showChallengePanel;
</script>

<div>
  <img class="banner" src="./img/BANNER.jpg" alt="">
</div>
<div class="container">
  <div class="functions" on:click={() => showComponent("+")}>
    <img src="./img/sumar.png" alt="" />
    <p>Sumar</p>
  </div>
  <div class="functions" on:click={() => showComponent("-")}>
    <img src="./img/restar.png" alt="" />
    <p>Restar</p>
  </div>
  <div class="functions" on:click={() => showComponent("*")}>
    <img src="./img/multiplicar.png" alt="" />
    <p>Multiplicar</p>
  </div>
  <div class="functions" on:click={() => showComponent("/")}>
    <img src="./img/dividir.png" alt="" />
    <p>Dividir</p>
  </div>
  <div class="button" on:click={showChallengePanel}>Voler Atras</div>
</div>

<style>
  .banner{
    width: 50%;
    height: 150px;
  }
  .container {
    height: auto;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
    gap: 1em;
  }
  .functions {
    background-color: #fff;
    border-radius: 5px;
    padding: 1em;
    box-shadow: 0 0 3px #fff;
  }
  img {
    height: 100px;
    width: 100px;
  }
  p {
    margin: 0;
    color: #111;
    font-weight: bold;
  }
  .button {
    width: 85%;
    padding: 1em;
    background-color: rgb(116, 230, 11);
    border-radius: 5px;
    font-weight: bold;
    font-size: 1em;
  }
</style>
