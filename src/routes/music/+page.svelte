<script>
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

    let isPlaying = true;

    var timerObj = setInterval(counter, 100);

    function togglePlaying() {
        if (isPlaying) {
            clearInterval(timerObj);
            timerObj = null;
        } else {
            timerObj = setInterval(counter, 100);
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
    
</script>

<svelte:window bind:innerWidth={width} bind:innerHeight={height} />

<div class="no-scroll">
    {#if isPlaying}
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
    {/if}

    <div class="col">
        {#each Array(calcSize(height)) as _, ind (ind)}
            <div>
                {#each Array(calcSize(width)) as _, index (index)}
                    <span
                        class="material-symbols-outlined button, heart"
                        class:peak={index == i % calcSize(width)}
                        class:slope={index == (i - 1) % calcSize(width) ||
                            index == (i + 1) % 50}
                        class:slight={index == (i - 2) % calcSize(width) ||
                            index == (i + 2) % calcSize(width)}
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

    .peak {
        opacity: 1;
    }

    .slope {
        opacity: 0.5;
    }

    .slight {
        opacity: 0.25;
    }
</style>
