<script>
    import AnimatedBackground from "./AnimatedBackground.svelte";
    import Controller from "./+page.svelte";
    import { browser } from "$app/environment";

    let child;


    // Below is the code that controls the ticking for the animated background
    let rate = 100;

    // Counter variable starts at not 1 for an offset default
    let i = 155;

    function counter() {
        i += 1;
    }

    export let isPlaying = false;

    var timerObj;

    export function togglePlaying() {
        if (isPlaying) {
            clearInterval(timerObj);
            timerObj = null;
        } else {
            timerObj = setInterval(counter, rate);
        }
        isPlaying = !isPlaying;
    }


    if (browser) {
        document.addEventListener("keydown", (e) => {
            if (e.code === "Space") {
                togglePlaying();
            }
        });
    }
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
    <slot/>
</div>

<AnimatedBackground bind:this={child} count={i}/>

<style>
    .content {
        position: absolute;
        width: 100%;
        height: 100%;
        display: flex;
    }
</style>
