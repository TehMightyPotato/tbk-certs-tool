<script lang="ts">
    import { BasicTable } from "csv2table";
    let columnDelimiter: string = ",";
    export let csv: string;
</script>

<h2>Daten:</h2>
<form>
    <div>
        <label for="delimiterInput">Trennzeichen</label>
        <input id="delimiterInput" bind:value={columnDelimiter} />
    </div>
</form>
<h3>Tabelle:</h3>
<BasicTable {csv} csvColumnDelimiter={columnDelimiter} />

<style>
    form {
        display: table;
    }
    div {
        display: table-row;
    }
    label {
        display: table-cell;
    }
    input {
        display: table-cell;
    }
</style>
