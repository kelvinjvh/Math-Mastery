<script>
  export let toggleMathOperationComponent;
  export let toggleChallengePanel;
</script>

<div class="operation-panel">
  <div class="operation-row">
    <div class="operation-button" on:click={() => toggleMathOperationComponent("➕")}>
      <p class="operation-sign">➕</p>
      <p>Sumar</p>
    </div>
    <div class="operation-button" on:click={() => toggleMathOperationComponent("➖")}>
      <p class="operation-sign">➖</p>
      <p>Restar</p>
    </div>
    <div class="operation-button" on:click={() => toggleMathOperationComponent("✖")}>
      <p class="operation-sign">✖️</p>
      <p>Multiplicar</p>
    </div>
    <div class="operation-button" on:click={() => toggleMathOperationComponent("➗")}>
      <p class="operation-sign">➗</p>
      <p>Dividir</p>
    </div>
  </div>
  <div class="back-button" on:click={toggleChallengePanel}>⬅️ Volver Atras</div>
</div>

<style>
  .operation-panel {
    width: 100%;
    height: 60vh;
    display: grid;
    place-items: center;
    margin-top: 5em;
  }

  .operation-row {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 3em;
    margin-bottom: 3em;
  }
  .operation-button {
    background-color: var(--primary-color);
    border-radius: 5px;
    padding: 1em;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    height: 130px;
    width: 130px;
    display: grid;
    place-items: center;
  }
  p {
    margin: 0;
    color: #fff;
    font-size: 1em;
    font-weight: bold;
  }
  .operation-sign {
    font-size: 2.5em;
  }
  .back-button {
    width: 84%;
    padding: 1em;
    background-color: var(--primary-color);
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    border-radius: 5px;
    font-weight: bold;
    font-size: 1em;
    margin: 0 auto;
    text-align: center;
  }
</style>
