<script>
  import { link } from 'svelte-spa-router';
</script>
<div class="w-full h-90 flex justify-center items-center">
  <div class="mx-auto m-auto pt-17 lg:pt-0 text-center">
    <h1 class="text-6xl uppercase font-extrabold">
      Shinra <span class="text-red-500">Api</span>
    </h1>

    <p class="text-gray-600 italic mt-2 gap-2">
      Shinra API merupakan sahabat bagi para developer
      <br />
      tanpa limitasi, paywall, dan kunci API. Kami hadir dengan infrastruktur
      yang solid dan anonim.
    </p>
    <div class=" w-full pt-4 flex gap-5 justify-center h-auto">
      <a class="w-28 h-10 bg-red-500 p-2 rounded-xl mb-5 font-bold text-white" href="/docs" use:link>Get Started</a>
      <a class="w-28 h-10 bg-black p-2 rounded-xl mb-5 font-bold text-white" href="https://github.com/shinraapi/Shinraapi">Github</a>
    </div>
  </div>
</div>
<div class="w-full border border-b-black"></div>
