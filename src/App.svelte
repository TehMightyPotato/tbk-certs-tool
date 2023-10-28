<script lang="ts">
    import FileSelector from "./lib/FileSelector.svelte";
    import { readTextFile } from "@tauri-apps/api/fs";
    import ConfigView from "./lib/ConfigView.svelte";
    import CsvView from "./lib/CSVView.svelte";
    let dataFilePath: string;

    let csv: string;

    $: readTextFile(dataFilePath).then((result) => (csv = result));
</script>

<main class="container">
    <h1>TBK Zertifikats-Tool</h1>
    <a href="https://github.com" target="_blank">Hilfe und Support</a>
    <FileSelector bind:filePath={dataFilePath} />
    {#if dataFilePath != null}
        <ConfigView />
        {#if csv}
            <CsvView bind:csv />
        {:else}
            <p>Loading...</p>
        {/if}
    {/if}
</main>
