<script>
    import { onMount } from "svelte";
    export let ShowComponentCanvas;
    
    let canvas;
    let ctx;
    let drawing = false;

    // Iniciar dibujo (para mouse y touch)
    function startDrawing(event) {
        event.preventDefault();  // Previene el scroll en dispositivos móviles
        drawing = true;

        // Si es un evento de touch, obtener las coordenadas del toque
        const { offsetX, offsetY } = getCoordinates(event);
        ctx.beginPath();
        ctx.moveTo(offsetX, offsetY);
    }

    // Dibujar (para mouse y touch)
    function draw(event) {
        if (!drawing) return;

        // Obtener las coordenadas del evento
        const { offsetX, offsetY } = getCoordinates(event);
        ctx.lineTo(offsetX, offsetY);
        ctx.stroke();
    }

    // Terminar dibujo (para mouse y touch)
    function stopDrawing() {
        drawing = false;
        ctx.closePath();
    }

    // Obtener las coordenadas para eventos de mouse y touch
    function getCoordinates(event) {
        if (event.touches) {
            const touch = event.touches[0];
            const rect = canvas.getBoundingClientRect();
            return {
                offsetX: touch.clientX - rect.left,
                offsetY: touch.clientY - rect.top
            };
        } else {
            return {
                offsetX: event.offsetX,
                offsetY: event.offsetY
            };
        }
    }

    // Configurar el canvas cuando el componente se monta
    function setupCanvas() {
        ctx = canvas.getContext('2d');
        ctx.strokeStyle = 'black'; // Color de la línea
        ctx.lineWidth = 2;         // Ancho de la línea
    }

    // Hook de ciclo de vida para montar el canvas
    onMount(() => {
        setupCanvas();
    });
</script>

<div class="container_canvas">
    <div class="content_btn">
        <p class="btn_close" on:click={ShowComponentCanvas}>❌</p>
    </div>
    <canvas class="canvas"  bind:this={canvas} 
    width="500" 
    height="400"
    on:mousedown={startDrawing}
    on:mousemove={draw}
    on:mouseup={stopDrawing}
    on:mouseleave={stopDrawing}
    on:touchstart={startDrawing}
    on:touchmove={draw}
    on:touchend={stopDrawing}></canvas>
</div>

<style>
  .canvas {
    background-color: rgb(255, 232, 27);
    width: 100%;
    height: 100vh;
    position: absolute;
    top: 0;
    left: 0;
  }
  .content_btn{
    width: 100%;
    display: flex;
    justify-content: flex-end;
  }
  .btn_close{
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
