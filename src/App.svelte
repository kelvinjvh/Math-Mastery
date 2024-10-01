<script>
  import ChallengePanel from "./lib/Components/ChallengePanel.svelte";
  import Home from "./lib/Components/Home.svelte";
  import MathOperationHandler from "./lib/Components/MathOperationHandler.svelte";

  let ShowMathOperationComponent = false;
  let operationSymbol = "";
  let ShowOperationsPanel = true;
  let difficultyLevel;

  function toggleMathOperationComponent(symbol) {
    ShowMathOperationComponent = !ShowMathOperationComponent;
    operationSymbol = symbol;
  }

  function toggleChallengePanel(difficulty) {
    ShowOperationsPanel = !ShowOperationsPanel;
    difficultyLevel = difficulty;
  }

</script>

{#if ShowOperationsPanel}
  <ChallengePanel {toggleChallengePanel} />
{:else if ShowMathOperationComponent}
  <MathOperationHandler {operationSymbol} {toggleMathOperationComponent} {difficultyLevel} />
{:else}
  <Home {toggleMathOperationComponent} {toggleChallengePanel} />
{/if}
