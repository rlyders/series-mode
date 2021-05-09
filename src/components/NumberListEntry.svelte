<script>
    import NumberPad from "../components/NumberPad.svelte";
    export let nums = "";
</script>

<NumberPad bind:nums />
<div class="d-flex p-2 justify-content-center entered-nums">
    {#if nums}
        {nums.split("").join(" ")}
    {:else}
        <span class="tip">Use mouse, touch, keyboard, or number pad.</span>
    {/if}
</div>

<style>
    .entered-nums {
        color: #333;
        font-weight: bolder;
    }
    .tip {
        font-style: italic;
        color: #ccc;
    }
</style>
