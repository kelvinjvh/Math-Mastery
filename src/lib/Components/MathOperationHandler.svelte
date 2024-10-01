<script>
  import Canvas from "./Canvas.svelte";
  import OperationsMathComponet from "./OperationsMathComponet.svelte";

  let ListOperationsMath = [];
  let canvasVisible = false;
  export let operationSymbol;
  export let toggleMathOperationComponent;
  export let difficultyLevel;

  function showCanvasComponent() {
    canvasVisible = !canvasVisible;
  }

  function generateMathOperations(count) {
    ListOperationsMath = [];
    for (let index = 0; index < count; index++) {
      let n1 = Math.ceil(Math.random() * difficultyLevel);
      let n2 = Math.ceil(Math.random() * difficultyLevel);

      let correctAnswer;

      switch (operationSymbol) {
        case "➕":
          correctAnswer = n1 + n2;
          break;
        case "➖":
          n1 < n2 ? (correctAnswer = n2 - n1) : (correctAnswer = n1 - n2);
          break;
        case "✖":
          correctAnswer = n1 * n2;
          break;
        case "➗":
          // Asegurando que n2 no sea 0
          n1 = n2 * Math.ceil(Math.random() * 10); // Asegurando que n1 sea múltiplo de n2
          //n1 < n2 ? (correctAnswer = n2 / n1) : (correctAnswer = n1 / n2);
          correctAnswer = n1 / n2;
          break;
        default:
          break;
      }

      ListOperationsMath.push({
        n1,
        n2,
        answer: "",
        correctAnswer,
        feedback: "",
      });
    }
  }

  generateMathOperations(6);

  function AnswerVerification(number) {
    if (parseInt(number.correctAnswer) === parseInt(number.answer)) {
      number.feedback = "✅";
    } else {
      number.feedback = "❌";
    }
    ListOperationsMath = [...ListOperationsMath];
  }
</script>

{#if canvasVisible}
  <Canvas {showCanvasComponent} />
{:else}
  <OperationsMathComponet
    {ListOperationsMath}
    {operationSymbol}
    {toggleMathOperationComponent}
    {generateMathOperations}
    {AnswerVerification}
    {showCanvasComponent}
  />
{/if}
