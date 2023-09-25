<script>
    export let rate = 100;

    import { browser } from "$app/environment";
    let width = 1000;
    let height = 1000;
    if (browser) {
        width = window.innerWidth;
        height = window.innerHeight;
    }


    let i = 0;

    function counter() {
        i += 1;
    }

    export let isPlaying = true;

    var timerObj = setInterval(counter, rate);

    export function togglePlaying() {
        if (isPlaying) {
            clearInterval(timerObj);
            timerObj = null;
        } else {
            timerObj = setInterval(counter, rate);
        }
        isPlaying = !isPlaying;
    }

    function calcSize(dim) {
        return Math.floor(dim / 24);
    }

    if (browser) {
        document.addEventListener("keydown", (e) => {
            if (e.code === "Space") {
                togglePlaying();
            }
        });
    }

    function opacity(x, y, x_count, y_count, i) {
        if (x == i % x_count || y == i % y_count) {
            return 0.75;
        } else if (Math.abs(x - (i % x_count)) == 1 || Math.abs(y - (i % y_count)) == 1) {
            return 0.5;
        } else if (Math.abs(x - (i % x_count)) == 2 || Math.abs(y - (i % y_count)) == 2) {
            return 0.25;
        }
    }

</script>

<svelte:window bind:innerWidth={width} bind:innerHeight={height} />

<div class="no-scroll">
    <!-- {#if isPlaying}
        <button
            on:click={togglePlaying}
            class="material-symbols-outlined button"
        >
            pause
        </button>
    {:else}
        <button
            on:click={togglePlaying}
            class="material-symbols-outlined button"
        >
            play_arrow
        </button>
    {/if} -->

    <div class="col">
        {#each Array(calcSize(height)) as _, ind (ind)}
            <div>
                {#each Array(calcSize(width)) as _, index (index)}
                    <span
                        class="material-symbols-outlined button, heart"
                        style:opacity={opacity(index, ind,calcSize(width), calcSize(height), i)}
                    >
                        favorite
                    </span>
                {/each}
            </div>
        {/each}
    </div>
</div>

<style>
    .no-scroll {
        overflow: hidden;
        position: relative;
    }

    .col {
        display: flex;
        flex-direction: column;
    }

    .heart {
        color: #34006f;
        opacity: 0.13;
    }
</style>