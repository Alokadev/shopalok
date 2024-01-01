<script>
  import { page } from '$app/stores';
  import { goto } from '$app/navigation';
  import Icons from './Icons.svelte';

  let value = $page.url.searchParams.get('q');

  async function submit(e) {
    let query = new URLSearchParams();
    if (value) {
      query.set('q', value);
    }
    await goto(`/search${query ? `?${query}` : ''}`, { keepFocus: true });
  }
</script>

<form on:submit|preventDefault={submit} class="relative flex w-full items-center">
  <div class="absolute top-0 right-0 mr-2">
    <Icons strokeColor="black" type="search" />
  </div>
  <input
    id="searchInput"
    type="text"
    bind:value
    placeholder="Search for products..."
    autocomplete="off"
    class="w-full rounded-lg border bg-white px-4 py-2 text-sm text-black placeholder:text-neutral-500 dark:border-neutral-800 dark:bg-transparent dark:text-white dark:placeholder:text-neutral-400"
  />


</form>


<style>
  form {
    margin: 0px;
    padding: 0px;
    display: inline;
  }
  input::placeholder {
    color: rgb(85, 85, 85);
  }
</style>
