<script>
    import Footer from "../components/Footer.svelte";
    export let version = "0.0.1";
</script>

<div class="jumbotron">
    <div class="text-center">
        <h4>Series Mode <version>v{version}</version></h4>
        <p>This app finds the value that appears most frequently in a data set.</p>
    </div>

    <Footer />
</div>

<style>
    version {
        font-size: 14px;
        font-style: italic;
    }
    .jumbotron {
        padding: 2em;
        margin-bottom: 1em;
    }
</style>
