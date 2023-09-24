<script>
    let i = 0;

    function counter() {
        i += 1;
    }

    let isPlaying = true;

    var timerObj = setInterval(counter, 100);

    function stop() {
        if (timerObj) {
            clearInterval(timerObj);
            timerObj = null;
            isPlaying = false;
        }
    }

    // start timer using current settings (if it's not already running)
    function start() {
        if (timerObj == null) {
            timerObj = setInterval(counter, 100);
            isPlaying = true;
        }
    }
</script>

{#if isPlaying}
    <button on:click={stop} class="material-symbols-outlined button">
        pause
    </button>
{:else}
    <button on:click={start} class="material-symbols-outlined button">
        play_arrow
    </button>
{/if}

<div class="col">
    {#each Array(30) as _, ind (ind)}
        <div>
            {#each Array(50) as _, index (index)}
                <span
                    class="material-symbols-outlined button, heart"
                    class:peak={index == i % 50}
                    class:slope={index == (i - 1) % 50 || index == (i + 1) % 50}
                    class:slight={index == (i - 2) % 50 ||
                        index == (i + 2) % 50}
                >
                    favorite
                </span>
            {/each}
        </div>
    {/each}
</div>

<style>
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
