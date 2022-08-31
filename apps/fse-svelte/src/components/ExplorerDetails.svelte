<script>
  import { fileSystemExplorerStore } from "shared-fse-data";

  const detailsContent = fileSystemExplorerStore.getFilesByActiveDir();
</script>

<div class="fse-explorer__details table table-auto w-full" />

{#if detailsContent}
  <div class="fse-explorer-row__header table-header-group">
    <div class="table-row">
      <div class="table-cell text-left py-3 px-9">Name</div>
      <div class="table-cell text-left py-3">Date Modifed</div>
      <div class="table-cell text-left py-3">File Size</div>
    </div>
  </div>
{/if}

<style>
   :global(.fse-explorer__details:nth-child(2) .table-cell) {
    padding-top: 15px;
  }

  :global(.fse-explorer-row .fse-folder,
  .fse-file) {
    padding-left: 15px;
    padding-top: 10px;
    padding-bottom: 10px;
  }

  :global(.fse-explorer-row:hover) {
    background-color: #e6e6e6;
  }

  :global(.fse-explorer-row .fse-folder-detail:hover) {
    background: none;
  }

  .fse-explorer-row__header {
    color: rgb(132, 132, 132);
  }

  .fse-explorer-row__header .table-row {
    height: 50px;
  }

  .fse-explorer-row__header .table-cell {
    border-bottom: 1px solid var(--primary-grey);
  }
</style>
