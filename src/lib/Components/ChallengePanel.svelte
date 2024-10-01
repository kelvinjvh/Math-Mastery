<script>
  export let toggleChallengePanel;
</script>

<div class="challenge-panel">
  <h1 class="challenge-title">¡Desafía tu Mente Matemática!</h1>
  <div class="operation-symbols">
    <span>➕</span><span>➖</span>
    <span>❌</span><span>➗</span>
    <span>❓</span><span>🧠</span>
    <span>🤔</span>
  </div>
  <div class="challenge-center">
    <div class="challenge-button" on:click={() => toggleChallengePanel(10)}>
      <span>Fácil 😀</span>
    </div>
    <div class="challenge-button" on:click={() => toggleChallengePanel(30)}>
      <span>Intermedio 🤔</span>
    </div>
    <div class="challenge-button" on:click={() => toggleChallengePanel(80)}>
      <span>Avanzado 🚀</span>
    </div>
    <div class="challenge-button" on:click={() => toggleChallengePanel(100)}>
      <span>Experto 🧠</span>
    </div>
  </div>
</div>

<style>
  .challenge-panel {
    width: 100%;
    margin: 1.5em auto;
    display: grid;
    place-items: center;
    gap: 2em;
  }
  .challenge-title{
    font-size: 1.6em;
    margin: 0;
    padding: 0 .1em;
  }
  .operation-symbols {
    display: flex;
    justify-content: space-between;
    font-size: 1.8em;
    width: 100%;
  }
  .challenge-center {
    display: grid;
    place-items: center;
    width: 100%;
  }

  .challenge-button {
    padding: 1em;
    border-radius: 8px; /* Aumenté el radio para un efecto más suave */
    background-color: #ffc107;
    color: #f5f5f5;
    font-weight: bold;
    font-size: 1.5em;
    width: 90%;
    margin: 0 auto 1.8em;
    text-align: center; /* Cambié a 'center' para centrar el texto */
    display: grid;
    place-items: center;
  }

  .challenge-button:hover {
    transform: scale(1.1);
    background-color: #ffa000; /* Cambio de color al pasar el mouse */
  }

  span {
    width: 70%;
  }
</style>
