<script>
  import { onMount } from "svelte";

  export let ShowComponentCanvas;
  let canvas;
  let ctx; // Solo declara ctx aquí

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
    ctx.beginPath();
    ctx.moveTo(x, y);
  }

  function ClearCanvas(){
    ctx.clearRect(0, 0, canvas.width, canvas.height);
  }

</script>

<div class="container_canvas">
  <div class="content_btn">
    <p class="btnClear" on:click={ClearCanvas}>🔄</p>
    <p class="btn_close" on:click={ShowComponentCanvas}>❌</p>
  </div>
  
</div>
<canvas
    bind:this={canvas}
    on:touchstart={startPosition}
    on:touchend={finishedPosition}
    on:touchmove={draw}
    class="canvas"
  ></canvas>

<style>
  .container_canvas {
    height: 95vh; /* Ocupa toda la altura de la ventana */
    width: 100vw; /* Ocupa todo el ancho de la ventana */
    position: relative; /* Para poder posicionar el botón correctamente */
    overflow: hidden; /* Para evitar desplazamiento */
  }

  .canvas {
    background-color: rgb(255, 232, 27);
    position: absolute;
    top: 0;
    left: 0;
    width: 100%; /* Asegúrate de que el canvas ocupe el 100% del contenedor */
    height: 100%; /* Asegúrate de que el canvas ocupe el 100% del contenedor */
  }

  .content_btn {
    width: 90%;
    margin: 0 auto;
    display: flex;
    justify-content: space-between;
    position: relative; /* Para posicionar el botón dentro de este contenedor */
    z-index: 10; /* Asegura que esté sobre el canvas */
  }
  .btnClear{
   padding:0 .8em;
   background-color: #222;
   border-radius: 5px;
   font-weight: bold;
   font-size: 2em;
   cursor: pointer;
  }
  .btn_close {
    height: 50px;
    width: 50px;
    background-color: #333;
    border-radius: 50%;
    display: grid;
    place-items: center;
    font-size: 1.5em;
  }
</style>
