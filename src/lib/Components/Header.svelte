<script>
    export let showCanvasComponent;
</script>
<div class="header">
    <div class="pencil" on:click={showCanvasComponent}>✏️</div>
</div>

<style>
    .header{
        width: 90%;
        display: flex;
        align-items: flex-end;
        justify-content: flex-end;
        font-size: 1.5em;
        margin: 1em auto;
    }
    .pencil{
        border-radius: 50%;
        height: 40px;
        width: 40px;
        background-color: #fff;
        display: grid;
        place-items: center;
        font-size: .9em;
        cursor: pointer;
        box-shadow: 0 0 5px #fff;
    }
</style>