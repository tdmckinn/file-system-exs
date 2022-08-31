<script>
  import { fileSystemExplorerStore } from "shared-fse-data";

  import CaretDownIcon from "./CaretDownIcon.svelte";
  import CaretRightIcon from "./CaretRightIcon.svelte";
  import FileIcon from "./FileIcon.svelte";
  import FolderIcon from "./FolderIcon.svelte";

  export let node;
  export let canExpand = true;
  let isSubFolderExpanded = false;

  function handleClick(e, node) {
    e.stopPropagation();
    console.log(e, node)
    // if (fileSystemExplorerStore.activeFileDir !== node.name) {
    //   fileSystemExplorerStore.activeFileDir = node.name;

    //   removeExplorerRows();
    //   addExplorerRows();
    // }
  }
</script>

<!-- * Example rendered UI
<ul>
  <li class="collapsed has-children">Files
     <ul>
      <li class="collapsed">Documents
        <ul>
        <li>Git</li>
        <li>Images</li>
        <li>System</li>
      </ul>
      </li>
      <li>Images</li>
      <li>System</li>
    </ul>
  </li>
</ul> -->

{#if node}
  {#if node.type === "file"}
    <li class="fse-file">
      <span><FileIcon /></span>
    </li>
  {:else if node.isParent() && canExpand}
    <li
      class="fse-folder has-children collapsed"
      on:click={(e) => handleClick(e, node)}
    >
      <span class="fse-folder-detail fse-folder-wIcon">
        <span class="fse-collapse__icon" style="width: 15px; height: 15px;">
          {#if isSubFolderExpanded}
            <CaretDownIcon />
          {:else}
            <CaretRightIcon />
          {/if}
        </span>
        <FolderIcon className="folder-icon" />
        {node.name}
      </span>
      <ul class="fse-folder-contents is-visible">
        {#each node.children as child}
          <svelte:self node={child} />
        {/each}
      </ul>
    </li>
  {:else}
    <li class="fse-folder">
      <span class="fse-folder-detail fse-folder-wIcon">
        <FolderIcon className="folder-icon" />
        {node.name}
      </span>
    </li>
  {/if}
{/if}

<style>
  .fse-folder,
  .fse-file {
    display: flex;
    flex-direction: column;
    list-style: none;
  }

  .fse-folder-detail:hover {
    background-color: #dfdfdf;
  }

  .fse-folder-wIcon {
    display: flex;
    align-items: center;
  }

  :global(.fse-folder-detail svg) {
    cursor: pointer;
    width: 16px;
    height: 16px;
    margin-right: 5px;
  }

  .fse-collapse__icon {
    margin-right: 5px;
  }

  :global(.fse-folder-contents) {
    display: none;
  }

  :global(.fse-folder-contents.is-visible) {
    display: block;
  }

  .fse-file {
    display: flex;
    justify-content: center;
  }

  :global(.fse-file svg) {
    height: 15px;
    width: 15px;
    margin-right: 5px;
  }

  .fse-file span {
    display: flex;
    align-items: center;
  }
</style>
