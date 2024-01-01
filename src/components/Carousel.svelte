<script>
  export let items = [];
</script>

<div class="slider relative w-full overflow-scroll bg-light mt-5">
  <div class="slide-track flex">
    {#each items as item (item.node.id)}
      <a
        data-sveltekit-prefetch
        href={`/product/${item.node.handle}`}
        class="slide relative h-[40vh] flex-none md:w-1/3"
      >
        <img
          alt={item.node.title}
          class="h-full"
          decoding="async"
          loading="lazy"
          src={item.node.images.edges[0].node.originalSrc}
        />

        <div class="absolute center-0 bottom-0 m-3 overflow-hidden">
          <div
            class="flex items-center rounded-full border bg-white/70 p-1 text-xs font-semibold text-black backdrop-blur-md dark:border-neutral-800 dark:bg-black/70 dark:text-white"
          >
            <h3 class="mr-4 line-clamp-2 flex-grow pl-2 leading-none tracking-tight">
              {item.node.title}
            </h3>
            <div class="flex-none rounded-full bg-blue-600 p-2 text-white">
              $ 25
              <div class="hidden @[275px]/label:inline">$</div>
            </div>
          </div>
        </div>
      </a>
    {/each}
  </div>
</div>

<style>
  @-webkit-keyframes scroll {
    0% {
      -webkit-transform: translateX(0);
      transform: translateX(0);
    }
    100% {
      -webkit-transform: translateX(calc(-250px * 7));
      transform: translateX(calc(-250px * 7));
    }
  }

  @keyframes scroll {
    0% {
      -webkit-transform: translateX(0);
      transform: translateX(0);
    }
    100% {
      -webkit-transform: translateX(calc(-250px * 7));
      transform: translateX(calc(-250px * 7));
    }
  }

  .slider::after {
    -webkit-transform: rotateZ(180deg);
    transform: rotateZ(180deg);
  }

  .slider .slide-track {
    -webkit-animation: scroll 40s linear infinite;
    animation: scroll 40s linear infinite;
  }
</style>
