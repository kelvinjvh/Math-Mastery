<script>
  export let showChallengePanel;
</script>

<div class="panel">
  <div class="center">
    <div class="button" on:click={() => showChallengePanel(10)}><span>Facil 😀</span></div>
    <div class="button" on:click={() => showChallengePanel(30)}><span>Intermedio 🤔</span></div>
    <div class="button" on:click={() => showChallengePanel(60)}><span>Avanzado 🚀</span></div>
    <div class="button" on:click={() => showChallengePanel(100)}><span>Experto 🧠</span></div>
  </div>
</div>

<style>
  .panel {
    width: 100%;
    margin: 0 auto;
    height: 100vh;
    display: grid;
    place-items: center;
  }
  .center{
    display: grid;
    place-items: center;
    width: 100%;
  }
  .button {
    padding: 1em;
    border-radius: 5px;
    background-color: rgb(33, 150, 43);
    color: #fff;
    font-weight: bold;
    font-size: 1.5em;
    transition: 0.5s;
    width: 90%;
    margin: 0 auto 1em;
    text-align: start;
    display: grid;
    place-items: center;
  }
  span{
    width: 70%;
  }
  .button:hover {
    transform: scale(1.1);
  }
</style>
