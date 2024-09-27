<script>
    export let ShowComponentCanvas;
</script>
<div class="header">
    <div class="pencil" on:click={ShowComponentCanvas}>✏️</div>
</div>

<style>
    .header{
        width: 100%;
        display: flex;
        align-items: flex-end;
        justify-content: flex-end;
        font-size: 1.5em;
        
    }
    .pencil{
        border-radius: 50%;
        height: 60px;
        width: 60px;
        background-color: #fff;
        display: grid;
        place-items: center;
        font-size: 1.3em;
        cursor: pointer;
        box-shadow: 0 0 5px #fff;
    }
</style>