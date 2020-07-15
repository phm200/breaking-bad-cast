<script>
  import Header from './Header.svelte'
  import CharacterGrid from './CharacterGrid.svelte'
  import Search from './Search.svelte'
  import { onMount } from 'svelte'
  let items = []

  onMount(async () => await searchFunction(''))

  async function searchFunction(searchTerm) {
    // empty items array to show spinner while doing query
    items = []
    const res = await fetch(
      `https://www.breakingbadapi.com/api/characters?name=${searchTerm}`
    )
    items = await res.json()
  }

  async function handleNewSearchTerm(event) {
    let newSearchTerm = event.detail
    await searchFunction(newSearchTerm)
  }
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
  <Search on:search={handleNewSearchTerm} />
  <CharacterGrid {items} />
</div>
