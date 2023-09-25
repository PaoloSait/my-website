<script>
    import AnimatedBackground from "./AnimatedBackground.svelte";

    let child;
    let isPlaying = false;
</script>
<!-- 
{#if isPlaying}
    <button
        on:click={() => child.togglePlaying()}
        class="material-symbols-outlined button"
    >
        pause
    </button>
{:else}
    <button
        on:click={() => child.togglePlaying()}
        class="material-symbols-outlined button"
    >
        play_arrow
    </button>
{/if} -->

<div>
    <div class="controller">
        <p>Hello peter</p>
    </div>
    <AnimatedBackground bind:this={child} rate="100" />
</div>

<style>
    .controller {
        width: 300;
        height: 300;
        background-color: white;
        position: absolute;
    }
</style>
