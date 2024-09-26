<script>
    export let showChallengePanel;
</script>
<div class="panel">
    <div class="button" on:click={()=>showChallengePanel(10)}>Facil</div>
    <div class="button" on:click={()=>showChallengePanel(30)}>Intermedio</div>
    <div class="button" on:click={()=>showChallengePanel(60)}>Avanzado</div>
    <div class="button" on:click={()=>showChallengePanel(100)}>Experto</div>
</div>
<style>
    .panel{
        width: 90%;
        margin: 0 auto;
    }
    .button{
        padding: 1em;
        border-radius: 5px;
        background-color: rgb(116, 230, 11);
        color: #111;
        font-weight: bold;
        font-size: 1.2em;
        margin-bottom: 1em;
        transition: .5s;
    }
    .button:hover{
        transform: scale(1.1);
    }
</style>