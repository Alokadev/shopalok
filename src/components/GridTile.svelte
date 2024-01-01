<script>
  export let title = '';
  export let removeLabels = false;
  export let imageSrc;
  export let price = '';
  export let currencyCode = '';
  export let href = '';
  export let priority = 'lazy';

  let hover = false;
</script>

<div
  on:mouseenter={() => {
    hover = true;
  }}
  on:mouseleave={() => {
    hover = false;
  }}
  class="h-full w-full overflow-hidden"
>
  <a
    data-test="grid-tile"
    {href}
    data-sveltekit-prefetch
    class="focus:border-blue-500 focus:border-2 relative flex h-full w-full items-center justify-center"
  >
    <img
      alt={title}
      class={`w-full md:w-1/2 lg:w-full flex-none transition duration-300 ease-in-out ${
        hover ? 'scale-110' : ''
      }`}
      fetchpriority={priority === 'eager' ? 'high' : 'low'}
      decoding="async"
      loading={priority}
      src={imageSrc}
    />
    {#if !removeLabels}
<div class="absolute top-0 left-0 overflow-hidden">
  <div class="bg-gray-500 p-3 ml-1 mt-1 text-2xl font-medium text-white rounded-lg">
    {title}
  </div>
  <div class="w-fit bg-gray-900 ml-1 p-3 mt-3 text-sm text-white rounded-lg">
    ${price}
    {currencyCode}
  </div>
</div>

    {/if}
  </a>
</div>
