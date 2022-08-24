<script>
  import svelteLogo from "./assets/svelte.svg";
  import { fileSystemExplorerStore } from "shared-fse-data";
  import { onMount } from "svelte";
  import FileSystemExplorer from "./lib/FileSystemExplorer.svelte";

  onMount(async () => {
    await fileSystemExplorerStore.fetchFileExploreContents();
  });
</script>

<main>
  <header class="fse-header">
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite Logo" />
    </a>
    <a href="https://svelte.dev" target="_blank">
      <img src={svelteLogo} class="logo svelte" alt="Svelte Logo" />
    </a>
  </header>
  <FileSystemExplorer />
</main>

<style>
  .logo {
    height: 50px;
    padding: 5px;
    will-change: filter;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
</style>
