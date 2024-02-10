<script>
    import {createEventDispatcher} from "svelte";
    const dispatch = createEventDispatcher();

    export let buttonMode;
</script>

<button on:click={() => dispatch("changeMode", {mode: buttonMode}) }></button>