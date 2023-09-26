<script>
    export let rate = 100;

    import { browser } from "$app/environment";
    let width = 1000;
    let height = 1000;
    if (browser) {
        width = window.innerWidth;
        height = window.innerHeight;
    }

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

    function xCount(dim) {
        return Math.floor(dim / 24);
    }
    
    function yCount(dim) {
        return Math.ceil(dim / 28);
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

<body>
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
        {#each Array(yCount(height)) as _, ind (ind)}
            <div>
                {#each Array(xCount(width)) as _, index (index)}
                    <span
                        class="material-symbols-outlined button, heart"
                        style:opacity={opacity(index, ind, xCount(width), yCount(height), i)}
                    >
                        favorite
                    </span>
                {/each}
            </div>
        {/each}
    </div>
</body>

<style>
    body {
        overflow: hidden;
        position: relative;
        z-index: -1;
        padding: 0%;
        margin: 0%;
    }

    .col {
        display: flex;
        flex-direction: column;
        margin: auto;
    }

    .heart {
        color: #34006f;
        opacity: 0.13;
        padding: 0%;
    }
</style>