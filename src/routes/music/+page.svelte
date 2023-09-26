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

<div class="content">
    <div class="controller">
        <div class="cover-art" />
        <p>Hello World</p>
    </div>
</div>

<AnimatedBackground bind:this={child} rate="100" />

<style>
    .content {
        position: absolute;
        width: 100%;
        height: 100%;
        display: flex;
    }

    .controller {
        width: 400px;
        height: 450px;
        padding: 10px;
        background-color: white;
        position: relative;
        margin: auto;
        box-shadow: 0px 0px 0px 0px rgba(0, 0, 0, 0.15);
    }

    .cover-art {
        background-color: grey;
    }
</style>
