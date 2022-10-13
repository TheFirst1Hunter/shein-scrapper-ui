<main>
  <button on:click={increment}>
    count is {count}
  </button>

</main>

<script lang="ts">
  import DisplayName from './Display-name.svelte'
  let count: number = 0
  const increment = () => {
    count += 1
  }
</script>

{#if count<5}
<DisplayName name = "test" />
  
{/if}
