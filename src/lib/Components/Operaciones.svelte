<script>
  let listNumbers = [];
  export let operationSigno;
  export let showComponent;
  export let Rangodifficulty;

  function generateNumber(count) {
    listNumbers = [];
    for (let index = 0; index < count; index++) {
      let n1 = Math.ceil(Math.random() * Rangodifficulty);
      let n2 = Math.ceil(Math.random() * Rangodifficulty);

      let correctAnswer;

      switch (operationSigno) {
        case "+":
          correctAnswer = n1 + n2;
          break;
        case "-":
          n1 < n2 ? (correctAnswer = n2 - n1) : (correctAnswer = n1 - n2);
          break;
        case "*":
          correctAnswer = n1 * n2;
          break;
        case "/":
          // Asegurando que n2 no sea 0
          n1 = n2 * Math.ceil(Math.random() * 10); // Asegurando que n1 sea múltiplo de n2
          //n1 < n2 ? (correctAnswer = n2 / n1) : (correctAnswer = n1 / n2);
          correctAnswer = n1 / n2;
          break;
        default:
          break;
      }

      listNumbers.push({
        n1,
        n2,
        answer: "",
        correctAnswer,
        feedback: "",
      });
    }
  }

  generateNumber(6);

  function verification(number) {
    if (parseInt(number.correctAnswer) === parseInt(number.answer)) {
      number.feedback = "✅";
    } else {
      number.feedback = "❌";
    }
    listNumbers = [...listNumbers];
  }
</script>

<h2>Operaciones Matematicas :</h2>
<div class="box_operation">
  {#each listNumbers as number}
    {#if operationSigno === "-" && number.n1 < number.n2}
      <div class="box_datos">
        <p>{number.n2} {operationSigno} {number.n1}</p>
        =<input
          type="number"
          bind:value={number.answer}
          on:input={() => verification(number)}
        /> <span>{number.feedback}</span>
      </div>
    {:else}
      <div class="box_datos">
        <p>{number.n1} {operationSigno} {number.n2}</p>
        =<input
          type="number"
          bind:value={number.answer}
          on:input={() => verification(number)}
        /> <span>{number.feedback}</span>
      </div>
    {/if}
  {/each}
  <div class="box_button">
    <button on:click={showComponent}>Reiniciar</button>
    <button on:click={() => generateNumber(6)}>Siguiente</button>
  </div>
</div>

<style>
  .box_operation {
    width: 100%;
    margin-bottom: 1em;
    border-radius: 5px;

    color: #fff;
    padding: 0.2em;
    display: grid;
    place-items: center;
  }
  .box_datos {
    font-size: 1.5em;
    display: flex;
    justify-self: center;
    align-items: center;
    margin-bottom: 1em;
  }
  p {
    margin: 0;
    letter-spacing: 0.1em;
    width: 150px;
  }
  input {
    width: 60px;
    height: 30px;
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
  span {
    height: 20px;
    width: 20px;
  }
  .box_button {
    width: 100%;
  }
  button {
    background-color: rgb(116, 230, 11);
    color: #111;
    font-weight: bold;
    display: inline-block;
  }
</style>
