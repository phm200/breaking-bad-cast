<script>
  import { debounce } from 'lodash-es'
  import { createEventDispatcher } from 'svelte'
  const dispatch = createEventDispatcher()
  const handleInput = debounce((e) => {
    dispatch('search', text)
  }, 500)
  let text = ''
</script>

<section class="search">
  <form>
    <input
      type="text"
      class="form-control"
      placeholder="Search characters"
      bind:value={text}
      on:input={handleInput} />
  </form>
</section>
