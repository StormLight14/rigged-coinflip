<script lang="ts">
    import { fade } from 'svelte/transition';
    export let rigged = "off";

    const choices = ["heads", "tails"];
    const animation_length = 200;

    let flipResult;
    let showFlipButton = true;
    let showResetButton = false;
    let showCoin = false;

    function flipCoin() {
        if (rigged != "off") {
            flipResult = rigged;
        } else {
            flipResult = choices[Math.floor(choices.length * Math.random())];
        }

        showCoin = true;
        showFlipButton = false;

        setTimeout(() => {
            showResetButton = true;
        }, animation_length / 2);
    }

    function reset() {
        showCoin = false;
        showResetButton = false;

        setTimeout(() => {
            showFlipButton = true;
        }, animation_length / 2);
    }
</script>

{#if showFlipButton}
    <button transition:fade={{delay: 0, duration: animation_length / 2}} on:click={flipCoin}>
        Flip a coin!
    </button>
{/if}

{#if showResetButton}
    <button transition:fade={{delay: 0, duration: animation_length / 2}} on:click={reset}>
        Reset
    </button>
{/if}

{#if showCoin}
    <div>
        <img transition:fade={{delay: 0, duration: animation_length}} src="/coin-{flipResult}.png" alt="Coin" width="200"/>
    </div>
{/if}


<p>
    {#if rigged != "off" && rigged != "heads" && rigged != "tails"}
        Coin has invalid rig mode: {rigged}
    {/if}
</p>