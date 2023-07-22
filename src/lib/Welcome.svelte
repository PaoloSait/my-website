<script>
    import { browser } from "$app/environment";
    let width = 1000;
    if (browser) {
        width = window.innerWidth;
    }
    let isMobile = width < 900;
</script>

<!-- Make our width variable dynamically update ("bind") to the window width-->
<svelte:window bind:innerWidth={width} />

<div class="body" class:mobile={width < 900}>
    <div class="content">
        <div style="height: 3vh;" />

        <p class="name">PAOLO SAIT</p>

        <p class="ramble">
            THIS WEBSITE IS STILL BEING CREATED. BE PATIENT TO SEE WHAT IT
            BECOMES IN THE FUTURE. FOR NOW PLEASE JUST ENJOY THE TRANQUILITY.
        </p>
    </div>
</div>

<style>
    @import url("https://fonts.googleapis.com/css?family=Bebas+Neue");

    * {
        font-family: "Bebas Neue";
        margin: 0px;
    }

    .name {
        color: #000000;
        font-size: 180px;
        font-style: normal;
        font-weight: 400;
        line-height: 180px;
        letter-spacing: 4px;
        display: flex;
        justify-content: center;
    }

    .ramble {
        font-size: 90px;
        font-style: normal;
        font-weight: 400;
        line-height: 90px; /* 100% */
        letter-spacing: 2px;
        background: linear-gradient(146deg, #d1d0d1 0%, #d0cad8 100%);
        background-clip: text;
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
    }

    .content {
        width: 650px;
        display: flex;
        justify-content: center;
        flex-direction: column;
    }

    .body {
        width: 100vw;
        display: flex;
        justify-content: center;
    }

    .mobile .name {
        font-size: 80px;
        font-style: normal;
        font-weight: 400;
        line-height: 80px;
        letter-spacing: 2px;
    }

    .mobile .ramble {
        font-size: 40px;
        font-style: normal;
        font-weight: 400;
        line-height: 40px;
        letter-spacing: 2px;
    }

    .mobile .content {
        width: 300px;
    }
    /* 
    .mobile .name{
        font-size: 50px;
        font-style: normal;
        font-weight: 400;
        line-height: 50px;
        letter-spacing: 2px;
    } */
</style>
