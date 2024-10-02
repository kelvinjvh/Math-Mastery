<script>
  import Header from "./Header.svelte";
  export let AnswerVerification;
  export let operationSymbol;
  export let ListOperationsMath;
  export let toggleMathOperationComponent;
  export let generateMathOperations;
  export let showCanvasComponent;
</script>

<Header {showCanvasComponent} />
<h2 class="title">Operaciones Matemáticas!!</h2>
<div class="operation-container">
  {#each ListOperationsMath as mathOperation}
    {#if operationSymbol === "➖" || (operationSymbol === "✖" && mathOperation.n1 < mathOperation.n2)}
      <div class="operation-item">
        <p>
          {mathOperation.n2} <span>{operationSymbol}</span>
          {mathOperation.n1}
        </p>
        =<input
          type="number"
          bind:value={mathOperation.answer}
          on:input={() => AnswerVerification(mathOperation)}
        />
        <span
          >{mathOperation.feedback === "" ? "❓" : mathOperation.feedback}</span
        >
      </div>
    {:else}
      <div class="operation-item">
        <p>
          {mathOperation.n1} <span>{operationSymbol}</span>
          {mathOperation.n2}
        </p>
        =<input
          type="number"
          bind:value={mathOperation.answer}
          on:input={() => AnswerVerification(mathOperation)}
        />
        <span class="feedback"
          >{mathOperation.feedback === "" ? "❓" : mathOperation.feedback}</span
        >
      </div>
    {/if}
  {/each}
  <div class="button-container">
    <button on:click={toggleMathOperationComponent}>Reiniciar 🔄</button>
    <button on:click={() => generateMathOperations(6)}>Siguiente 👉</button>
  </div>
</div>

<style>
  .title {
    text-align: center;
    font-size: 1.5em;
    margin-bottom: 1em;
    color: #fff; /* Asegúrate de que el color del texto sea legible */
  }

  .operation-container {
    width: 100%;
    margin-bottom: 1em;
    border-radius: 5px;
    color: #fff;
    display: grid;
    place-items: center;
  }

  .operation-item {
    font-size: 1.8em;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    margin-bottom: 0.4em;
    width: 100%;
    border-radius: 3px;
    padding: 0.3em;
  }

  .operation-item p {
    margin: 0;
    width: 150px;
    font-weight: bold;
  }

  .operation-item span {
    font-size: 0.7em;
  }

  input {
    width: 70px;
    height: 40px;
    border: none;
    outline: none;
    background-color: #fff;
    border-radius: 5px;
    text-align: center;
    color: #111;
    margin-left: 0.7em;
    font-size: 0.8em;
    font-weight: bold;
  }

  .feedback {
    width: 20px;
    font-size: 1em;
  }

  .button-container {
    width: 100%;
    display: flex;
    justify-content: space-evenly; /* Distribuye los botones con espacio entre ellos */
  }

  button {
    background-color: var(--secondary-color);
    color: #fff;
    font-weight: bold;
    display: inline-block;
    font-size: 1.2em;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    border: none; /* Añadido para eliminar borde predeterminado */
    border-radius: 5px; /* Bordes redondeados para los botones */
    padding: 0.5em 1em; /* Padding para los botones */
    cursor: pointer; /* Cambia el cursor al pasar sobre el botón */
  }
</style>
