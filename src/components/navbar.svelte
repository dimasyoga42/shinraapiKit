<script>
  import { link } from 'svelte-spa-router';

  let isOpen = $state(false);

  const handlerOpen = () => {
    isOpen = !isOpen;
  };

  const closeMenu = () => {
    isOpen = false;
  };
</script>

<header class="fixed top-0 left-0 z-50 w-full h-16 bg-white border-b border-gray-100">
  <div class="w-full h-full flex items-center justify-between">
    <div class="flex items-center gap-1 ml-2">
      <a href="/" use:link aria-label="Shinra API" onclick={closeMenu}>
        <img
          src="https://i.pinimg.com/736x/61/44/f0/6144f0ce1b33b5abe07cba04d2990d77.jpg"
          alt="Shinra API"
          class="w-12 h-12 object-cover rounded-full border border-red-500"
        />
      </a>

      <a
        href="/"
        use:link
        onclick={closeMenu}
        class="ml-2 font-extrabold uppercase cursor-pointer"
      >
        Shinra<span class="text-red-500">api</span>
      </a>
    </div>

    <div class="flex items-center h-full">
      <nav class="hidden md:flex items-center gap-6 mr-8">
        <a
          href="/"
          use:link
          class="transition-colors hover:text-red-500"
        >
          Home
        </a>

        <a
          href="/docs"
          use:link
          class="transition-colors hover:text-red-500"
        >
          Docs
        </a>

        <a
          href="https://shinraapi.betteruptime.com/"
          target="_blank"
          rel="noopener noreferrer"
          class="transition-colors hover:text-red-500"
        >
          Monitor
        </a>
      </nav>

      <button
        type="button"
        onclick={handlerOpen}
        aria-expanded={isOpen}
        aria-label={isOpen ? 'Close menu' : 'Open menu'}
        class="md:hidden mr-4 p-2 text-black hover:text-red-500 transition-colors"
      >
        {#if isOpen}
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            class="w-6 h-6"
          >
            <path stroke-linecap="round" stroke-linejoin="round" d="M6 18 18 6M6 6l12 12" />
          </svg>
        {:else}
          <svg
            xmlns="http://www.w3.org/2000/svg"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            class="w-6 h-6"
          >
            <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
          </svg>
        {/if}
      </button>

      <a
        href="https://github.com/shinraapi/Shinraapi"
        aria-label="Shinra API GitHub"
        title="Shinra API GitHub"
        target="_blank"
        rel="noopener noreferrer"
        class="mr-5 transition-opacity hover:opacity-70"
      >
        <img
          src="/github.png"
          alt="GitHub"
          class="w-6 h-6"
        />
      </a>
    </div>
  </div>

  {#if isOpen}
    <nav
      class="absolute top-16 left-0 w-full bg-white border-t border-gray-100 shadow-md md:hidden"
    >
      <div class="flex flex-col items-center gap-5 py-5">
        <a
          href="/"
          use:link
          onclick={closeMenu}
          class="transition-colors hover:text-red-500"
        >
          Home
        </a>

        <a
          href="/docs"
          use:link
          onclick={closeMenu}
          class="transition-colors hover:text-red-500"
        >
          Docs
        </a>

        <a
          href="https://shinraapi.betteruptime.com/"
          target="_blank"
          rel="noopener noreferrer"
          onclick={closeMenu}
          class="transition-colors hover:text-red-500"
        >
          Monitor
        </a>
      </div>
    </nav>
  {/if}
</header>
