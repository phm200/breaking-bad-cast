<script>
  import CharacterItem from './CharacterItem.svelte'
  import Spinner from './Spinner.svelte'
  export let items = []
</script>

{#if items && items.length > 0}
  <section class="cards">
    {#each items as item (item.char_id)}
      <CharacterItem {item} />
    {/each}
  </section>
{:else}
  <Spinner />
{/if}
