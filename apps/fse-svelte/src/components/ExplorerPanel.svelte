<script>
  import { fileSystemExplorerStore } from "shared-fse-data";
  import FileFolderNode from "./FileFolderNode.svelte";
</script>

<div class="fse-explorer__panel">
  {#if fileSystemExplorerStore.contents}
    <ul>
      <FileFolderNode node={fileSystemExplorerStore.contents} />
    </ul>
  {/if}
</div>

<style>
  .fse-explorer__panel {
    display: flex;
    flex-direction: column;
    padding-top: 10px;
    border-right: 1px solid var(--primary-grey);
  }

  :global(.fse-explorer__panel .fse-file.fse-file) {
    display: none;
  }

  :global(.fse-explorer__panel ul) {
    padding: 10px 0;
    padding-inline-start: 25px;
  }
</style>
