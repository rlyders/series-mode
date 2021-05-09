<script>
    import Header from "../components/Header.svelte";
    import Results from "../components/Results.svelte";
    import NumberListEntry from "../components/NumberListEntry.svelte";

    let version = "1.0.1";

    let nums = "";
</script>

<div id="wrap">
    <div id="main" class="container clear-top">
        <div class="d-flex flex-column">
            <Header {version} />
            <Results {nums} />
            <NumberListEntry bind:nums />
        </div>
    </div>
</div>
