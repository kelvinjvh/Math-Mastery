<script>
  import Header from "./Header.svelte";

  export let verification;
  export let operationSigno;
  export let listNumbers;
  export let showComponent;
  export let generateNumber;
  export let ShowComponentCanvas;
</script>

<Header {ShowComponentCanvas} />
<h2 class="title">Operaciones Matemáticas!!</h2>
<div class="operation-container">
  {#each listNumbers as number}
    {#if operationSigno === "➖" && number.n1 < number.n2}
      <div class="operation-item">
        <p>{number.n2} <span>{operationSigno}</span> {number.n1}</p>
        =<input
          type="number"
          bind:value={number.answer}
          on:input={() => verification(number)}
        /> <span>{number.feedback === "" ? "❓" : number.feedback}</span>
      </div>
    {:else}
      <div class="operation-item">
        <p>{number.n1} <span>{operationSigno}</span> {number.n2}</p>
        =<input
          type="number"
          bind:value={number.answer}
          on:input={() => verification(number)}
        />
        <span class="feedback"
          >{number.feedback === "" ? "❓" : number.feedback}</span
        >
      </div>
    {/if}
  {/each}
  <div class="button-container">
    <button on:click={showComponent}>Reiniciar 🔄</button>
    <button on:click={() => generateNumber(6)}>Siguiente 👉</button>
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
  background-color: #38b48b;
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

button:hover {
  background-color: #32a574; /* Color más oscuro al pasar el ratón */
}

</style>
