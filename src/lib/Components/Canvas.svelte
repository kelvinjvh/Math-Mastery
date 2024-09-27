<script>
  import { onMount } from 'svelte';

export let ShowComponentCanvas;
let canvas;
let ctx; // Solo declara ctx aquí

let painting = false;

// Configurar el canvas cuando el componente se monte
onMount(() => {
  ctx = canvas.getContext("2d");
  canvas.height = window.innerHeight * 0.5; // Ajusta el tamaño como prefieras
  canvas.width = window.innerWidth * 0.8;   // Ajusta el tamaño como prefieras
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

  if (e.type === "mousemove") {
    x = e.clientX - canvas.offsetLeft;  // Ajusta para la posición relativa
    y = e.clientY - canvas.offsetTop;
  } else if (e.type === "touchmove") {
    const touch = e.touches[0];
    x = touch.clientX - canvas.offsetLeft;
    y = touch.clientY - canvas.offsetTop;
  }

  ctx.lineTo(x, y);
  ctx.stroke();
  ctx.beginPath();
  ctx.moveTo(x, y);
}
</script>

<div class="container_canvas">
  <div class="content_btn">
    <p class="btn_close" on:click={ShowComponentCanvas}>❌</p>
  </div>
  <canvas
    bind:this={canvas}
    on:touchstart={startPosition}
    on:touchend={finishedPosition}
    on:touchmove={draw}
    class="canvas"
  ></canvas>
</div>

<style>
  .canvas {
    background-color: rgb(255, 232, 27);
   
    position: absolute;
    top: 0;
    left: 0;
  }
  .content_btn {
    border: 1px solid red;
    width: 100%;
    display: flex;
    justify-content: flex-end;
  }
  .btn_close {
    position: relative;
    z-index: 10;
    height: 50px;
    width: 50px;
    background-color: #333;
    border-radius: 50%;
    display: grid;
    place-items: center;
    font-size: 1.5em;
  }
</style>
