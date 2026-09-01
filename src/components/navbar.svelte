<script>
  import { link } from 'svelte-spa-router';
</script>

<div class="w-full h-16 flex justify-between items-center">
  <div class="flex items-center gap-1 ml-2">
    <a href="/" use:link aria-label="Shinra API">
      <img
        src="https://i.pinimg.com/736x/61/44/f0/6144f0ce1b33b5abe07cba04d2990d77.jpg"
        alt="Shinra API"
        class="w-12 h-12 bg-cover rounded-full border border-red-500"
      />
    </a>

    <a href="/" use:link class="font-extrabold ml-2 uppercase cursor-pointer">
      Shinra<span class="text-red-500">api</span>
    </a>
  </div>

  <div class="flex items-center gap-6">
    <nav class="flex items-center gap-6">
      <a href="/" use:link class="hover:text-red-500">
        Home
      </a>

      <a href="/docs" use:link class="hover:text-red-500">
        Docs
      </a>
      <a href="https://shinraapi.betteruptime.com/" class="hover:text-red-500">
        Monitor
      </a>
    </nav>

    <a
      href="https://github.com/shinraapi/Shinraapi"
      aria-label="Shinra API GitHub"
      title="Shinra API GitHub"
      target="_blank"
      rel="noopener noreferrer"
      class="mr-5"
    >
      <img
        src="./github.png"
        alt=""
        class="w-6 h-6 lg:w-5 lg:h-5"
      />
    </a>
  </div>
</div>
