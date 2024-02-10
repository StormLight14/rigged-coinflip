<script lang="ts">
  import Coin from "./lib/Coin.svelte";
  import ModeButton from "./lib/ModeButton.svelte";

  let currentMode = "off";
  let hideRigButtons = false;

  function reset() {
    hideRigButtons = false;
  }
</script>

<main class="container">
  <h1>Totally Normal Coin Flipper</h1>

  <div class="row">
    <Coin rigged={currentMode} on:reset={reset}/>
    {#if hideRigButtons == false}
      <div class="rigcontainer">
        <ModeButton buttonMode={"off"} on:changeMode={(e) => {currentMode = e.detail.mode; hideRigButtons = true;}}/>
        <ModeButton buttonMode={"heads"} on:changeMode={(e) => {currentMode = e.detail.mode; hideRigButtons = true;}}/>
        <ModeButton buttonMode={"tails"} on:changeMode={(e) => {currentMode = e.detail.mode; hideRigButtons = true;}}/>
      </div>
    {/if}
  </div>
</main>
