<script>
  import Header from './Header.svelte'
  import CharacterGrid from './CharacterGrid.svelte'
  import { onMount } from 'svelte'
  let items = []

  onMount(async () => {
    const res = await fetch(`https://www.breakingbadapi.com/api/characters`)
    items = await res.json()
  })
</script>

<style>
  .container {
    max-width: 1100px;
    margin: auto;
    padding: 0 20px;
  }
</style>

<div class="container">
  <Header />
  <CharacterGrid {items} />
</div>
