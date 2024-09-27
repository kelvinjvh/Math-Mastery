<script>
  import Canvas from "./Canvas.svelte";
  import ListData from "./ListData.svelte";

  let listNumbers = [];
  let showCanvas = false;
  export let operationSigno;
  export let showComponent;
  export let Rangodifficulty;

  function ShowComponentCanvas(){
    showCanvas=!showCanvas;
  }

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

{#if showCanvas}
  <Canvas {ShowComponentCanvas}/>
{:else}
  <ListData
    {listNumbers}
    {operationSigno}
    {showComponent}
    {generateNumber}
    {verification}
    {ShowComponentCanvas}
  />
{/if}
