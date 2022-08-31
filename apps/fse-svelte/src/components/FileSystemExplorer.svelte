<script>
  import { fileSystemExplorerStore } from "shared-fse-data";
  // import { ExplorerDetails } from "./ExplorerDetails/ExplorerDetails";
  import ExplorerPanel from "./ExplorerPanel.svelte";
</script>

<section class="fse-main">
  <ExplorerPanel />
  <!-- <ExplorerDetails /> -->
</section>

<style>
  .fse-main {
    display: grid;
    grid-template-columns: 1fr 2fr;
    border: 1px solid var(--primary-grey);
    min-height: 400px;
  }
</style>
