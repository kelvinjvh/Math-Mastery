<script>
  import ChallengePanel from "./lib/Components/ChallengePanel.svelte";
  import Home from "./lib/Components/Home.svelte";
  import Operaciones from "./lib/Components/Operaciones.svelte";

  let component = false;
  let operationSigno = "";
  let ShowPanelOperations = true;
  let Rangodifficulty;

  function showComponent(signo) {
    component = !component;
    operationSigno = signo;
  }

  function showChallengePanel(difficulty) {
    ShowPanelOperations = !ShowPanelOperations;
    Rangodifficulty = difficulty;
    console.log(difficulty);
  }
</script>

{#if ShowPanelOperations}
  <ChallengePanel {showChallengePanel} />
{:else if component}
  <Operaciones {operationSigno} {showComponent} {Rangodifficulty}/>
{:else}
  <Home {showComponent} {showChallengePanel} />
{/if}
