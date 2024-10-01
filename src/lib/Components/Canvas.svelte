<script>
  import { onMount } from "svelte";

  export let showCanvasComponent;
  let canvas;
  let ctx; // Solo declara ctx aquí
  let colorPincel = "#fff";
  let painting = false;

  // Configurar el canvas cuando el componente se monte
  onMount(() => {
    ctx = canvas.getContext("2d");
    canvas.height = window.innerHeight; // Ajusta para que ocupe toda la altura
    canvas.width = window.innerWidth; // Ajusta para que ocupe todo el ancho
  });

  // Iniciar dibujo
  function startPosition(e) {
    painting = true;
    draw(e); // Llama a draw para comenzar inmediatamente
  }

  // Finalizar dibujo
  function finishedPosition() {
    painting = false;
    ctx.beginPath(); // Reinicia el path al terminar de dibujar
  }

  // Función para dibujar
  function draw(e) {
    if (!painting) return; // Solo dibuja si painting es true

    ctx.lineWidth = 4;
    ctx.lineCap = "round";

    let x, y;

    if (e.type === "touchmove") {
      const touch = e.touches[0];
      x = touch.clientX - canvas.offsetLeft;
      y = touch.clientY - canvas.offsetTop;
    }

    ctx.lineTo(x, y);
    ctx.stroke();
    ctx.strokeStyle=colorPincel;
    ctx.beginPath();
    ctx.moveTo(x, y);
  }

  function ClearCanvas(){
    ctx.clearRect(0, 0, canvas.width, canvas.height);
  }

</script>

<div class="canvas-container">
  <div class="button-panel">
    <p class="reset-button" on:click={ClearCanvas}>🔄</p>
    <form>
      <input type="color" bind:value={colorPincel}>
    </form>
    <p class="close-button" on:click={showCanvasComponent}>❌</p>
  </div>
</div>
<canvas
    bind:this={canvas}
    on:touchstart={startPosition}
    on:touchend={finishedPosition}
    on:touchmove={draw}
    class="drawing-canvas"
></canvas>

<style>
  .canvas-container {
    height: 95vh; /* Ocupa toda la altura de la ventana */
    width: 100vw; /* Ocupa todo el ancho de la ventana */
    position: relative; /* Para poder posicionar el botón correctamente */
    overflow: hidden; /* Para evitar desplazamiento */
  }

  .drawing-canvas {
    background-color: #1a1a3f;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%; /* Asegúrate de que el canvas ocupe el 100% del contenedor */
    height: 100%; /* Asegúrate de que el canvas ocupe el 100% del contenedor */
  }

  .button-panel {
    width: 90%;
    margin: 0 auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: relative; /* Para posicionar el botón dentro de este contenedor */
    z-index: 10; /* Asegura que esté sobre el canvas */
  }

  .reset-button {
    padding: 0 0.8em;
    background-color: var(--secondary-color);
    border-radius: 5px;
    font-weight: bold;
    font-size: 2em;
    cursor: pointer;
    transition: background-color 0.3s;
  }

  .close-button {
    height: 50px;
    width: 50px;
    background-color: var(--secondary-color);
    border-radius: 50%;
    display: grid;
    place-items: center;
    font-size: 1.5em;
    cursor: pointer;

  }
</style>

