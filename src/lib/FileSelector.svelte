<script lang="ts">
    import { open } from "@tauri-apps/api/dialog";
    // Open a selection dialog for image files
    export let filePath: string;
    async function onSelectButtonPressed() {
        filePath = (await open({
            multiple: false,
            filters: [
                {
                    name: "Tabelle",
                    extensions: ["csv"],
                },
            ],
        })) as string;
    }
</script>

<label for="table-select">Wähle die Tabelle mit den Daten aus:</label>
<button on:click={onSelectButtonPressed}
    >{!filePath ? "Datei auswählen!" : filePath}</button
>
