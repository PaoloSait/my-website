<script>
    let showLove = false;

    function makeLove() {
        showLove = true;
    }
</script>

<div class="body">
    {#if showLove}
        <p class="message">Love you too</p>
    {/if}
    <div style="width: 3px;" />
    <button on:click={makeLove} class="material-symbols-outlined button">
        favorite
    </button>
</div>

<style>
    @import url("https://fonts.googleapis.com/css?family=Inter");

    .body {
        display: flex;
        justify-content: right;
        width: 100vw;
        height: 48px;
    }

    .material-symbols-outlined {
        font-variation-settings: "FILL" 0, "wght" 800, "GRAD" 0, "opsz" 40;
    }

    .material-symbols-outlined:hover {
        font-variation-settings: "FILL" 1, "wght" 800, "GRAD" 0, "opsz" 40;
    }

    .material-symbols-outlined:active {
        transform: scale(1.2);
    }

    .button {
        background-color: transparent;
        cursor: pointer;
        padding: 5px;
        border: none;
        color: #34006f;
    }

    @keyframes love-message {
        from {
            color: transparent;
        }
        to {
            color: #34006f;
        }
    }

    .message {
        animation-name: love-message;
        animation-duration: 3s;
        animation-fill-mode: both;
        font-family: "Inter";
        font-weight: 800;
    }
</style>
