<script lang="ts">
  import Coin from "./lib/Coin.svelte";
  import ModeButton from "./lib/ModeButton.svelte";

  let currentMode = "off";
</script>

<main class="container">
  <h1>Totally Normal Coin Flipper</h1>

  <div class="row">
    <Coin rigged={currentMode}/>
    <ModeButton buttonMode={"off"} on:changeMode={(e) => {currentMode = e.detail.mode}}/>
    <ModeButton buttonMode={"heads"} on:changeMode={(e) => {currentMode = e.detail.mode}}/>
    <ModeButton buttonMode={"tails"} on:changeMode={(e) => {currentMode = e.detail.mode}}/>
  </div>
</main>
