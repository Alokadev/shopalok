<!-- YourComponent.svelte -->

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
  class="h-full w-full overflow-hidden gap-8 rounded-xl"
>
  <a
    {href}
    data-sveltekit-prefetch
    class="relative flex h-full w-full items-center justify-center focus:border-2 focus:border-blue-500 rounded-lg"
  >
    <img
      alt={title}
      class={`w-full flex-none transition duration-300 ease-in-out md:w-1/2 lg:w-full rounded-lg${
        hover ? 'scale-110' : ''
      }`}
      fetchpriority={priority === 'eager' ? 'high' : 'low'}
      decoding="async"
      loading={priority}
      src={imageSrc}
    />
    {#if !removeLabels}
      <div class="absolute left-0 top-0 overflow-hidden m-3">
        <div class="flex items-center rounded-full border bg-white/70 p-1 text-xs font-semibold text-black backdrop-blur-md dark:border-neutral-800 dark:bg-black/70 dark:text-white">
          <h3 class="mr-4 line-clamp-2 flex-grow pl-2 leading-none tracking-tight">{title}</h3>
          <div class="flex-none rounded-full bg-blue-600 p-2 text-white">
            ${price}
            <div class="hidden @[275px]/label:inline">{currencyCode}</div>
          </div>
        </div>
      </div>
   {/if}
  </a>
</div>
