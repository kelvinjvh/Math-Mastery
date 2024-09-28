<script>
  export let showChallengePanel;
</script>

<div class="challenge-panel">
  <div class="challenge-center">
    <div class="challenge-button" on:click={() => showChallengePanel(10)}><span>Fácil 😀</span></div>
    <div class="challenge-button" on:click={() => showChallengePanel(30)}><span>Intermedio 🤔</span></div>
    <div class="challenge-button" on:click={() => showChallengePanel(60)}><span>Avanzado 🚀</span></div>
    <div class="challenge-button" on:click={() => showChallengePanel(100)}><span>Experto 🧠</span></div>
  </div>
</div>


<style>
  .challenge-panel {
  width: 100%;
  margin: 0 auto;
  height: 100vh;
  display: grid;
  place-items: center;
}

.challenge-center {
  display: grid;
  place-items: center;
  width: 100%;
}

.challenge-button {
  padding: 1em;
  border-radius: 8px; /* Aumenté el radio para un efecto más suave */
  background-color: #FFC107;
  color: #F5F5F5;
  font-weight: bold;
  font-size: 1.5em;
  transition: transform 0.3s, background-color 0.3s; /* Agregué transición para el color de fondo */
  width: 90%;
  margin: 0 auto 1.8em;
  text-align: center; /* Cambié a 'center' para centrar el texto */
  display: grid;
  place-items: center;
}

.challenge-button:hover {
  transform: scale(1.1);
  background-color: #FFA000; /* Cambio de color al pasar el mouse */
}

span {
  width: 70%;
}

</style>