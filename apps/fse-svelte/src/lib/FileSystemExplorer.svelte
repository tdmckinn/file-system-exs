<script>
  import {fileSystemExplorerStore} from 'shared-fse-data'

  console.log(fileSystemExplorerStore)
  let count = 0
  const increment = () => {
    count += 1
  }
</script>

<button on:click={increment}>
  count is {count}
</button>
