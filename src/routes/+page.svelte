<script>
    import { fade } from 'svelte/transition'
    import Card from "../lib/comp/card.svelte"
    import { onMount } from 'svelte'

    let showText = true
    let blurBackground = true

    onMount(() => {
        setTimeout(() => {
            showText = false
            blurBackground = false
        }, 5000)
    })
</script>

<!-- <audio id="nyan" autoplay loop>
    <source src="src/lib/assets/nyan.mp3" type="audio/mpeg">
</audio> -->

<img src="src/lib/assets/bg.png" class="bg">

<div class="container">
    {#if showText}
        <div class="intro-text" out:fade={{ duration: 1000 }}>
            A long time ago<br>(last pearl ball)<br>in a galaxy far far away ...
        </div>
    {/if}

    <div class:blurred={blurBackground}>
        <Card/>
    </div>
</div>

<style>
    :global(body){
        background-color: rgb(24, 24, 24);
    }
    .container {
        text-align: center;
        display: grid;
        justify-content: center;
        align-items: center;
        height: 100vh;
        margin: 0;
        position: relative;
    }

    .intro-text {
        color: cyan;
        font-size: 2rem;
        text-align: center;
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        z-index: 2;
        text-shadow: 3px 3px black;
    }

    .blurred {
        transition: filter 1s ease-in-out;
        filter: blur(8px);
    }

    .bg {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        object-fit: cover;
        z-index: -1;
        filter: blur(5px) brightness(50%);
        transition: filter 1s ease-in-out;
    }
</style>
