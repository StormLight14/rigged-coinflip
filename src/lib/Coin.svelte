<script lang="ts">
    import { fade } from 'svelte/transition';

    const choices = ["heads", "tails"];
    export let rigged = "none";

    let flipResult = "heads";
    let showFlipButton = true;
    let showResetButton = false;
    let showCoin = false;

    function flipCoin() {
        if (rigged != "none") {
            flipResult = rigged;
        } else if (rigged == "none") {
            flipResult = choices[Math.floor(choices.length * Math.random())];
        }
        showCoin = true;
        showResetButton = true;
        showFlipButton = false;
    }

    function reset() {
        showCoin = false;
        showResetButton = false;
        showFlipButton = true;
    }
</script>

{#if showFlipButton}
    <button on:click={flipCoin}>
        Flip a coin!
    </button>
{/if}

{#if showResetButton}
    <button on:click={reset}>
        Reset
    </button>
{/if}

{#if showCoin}
    <div>
        <img transition:fade src="/coin-{flipResult}.png" alt="Coin" width="200"/>
    </div>
{/if}


<p>
    {#if rigged === "none"}
        Coin is not rigged to win.
    {:else if rigged === "heads"}
        Coin is rigged for Heads to win.
    {:else if rigged === "tails"}
        Coin is rigged for Tails to win.
    {:else}
        Coin has invalid thing
    {/if}
</p>