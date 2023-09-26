<script>
    export let count = 1;

    import { browser } from "$app/environment";
    let width = 1000;
    let height = 1000;
    if (browser) {
        width = window.innerWidth;
        height = window.innerHeight;
    }

    function xCount(dim) {
        return Math.floor(dim / 24);
    }
    
    function yCount(dim) {
        return Math.ceil(dim / 28);
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
    <div class="col">
        {#each Array(yCount(height)) as _, ind (ind)}
            <div>
                {#each Array(xCount(width)) as _, index (index)}
                    <span
                        class="material-symbols-outlined button, heart"
                        style:opacity={opacity(index, ind, xCount(width), yCount(height), count)}
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