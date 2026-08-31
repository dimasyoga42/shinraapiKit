<script>
  import { onMount } from 'svelte';

  let mapEl;
  let ipData = {
    ip: '—',
    protocol: '—',
    city: '—',
    region: '—',
    country: '—',
    isp: '—'
  };
  let loading = true;
  let error = null;

  // Ambil data IP + geolokasi. Ganti endpoint ini kalau mau pakai provider lain
  // (ipinfo.io, ip-api.com, dll) — sesuaikan nama field-nya juga.
  async function fetchIpInfo() {
    try {
      const res = await fetch('https://ipapi.co/json/');
      if (!res.ok) throw new Error('Gagal mengambil data IP');
      const data = await res.json();

      ipData = {
        ip: data.ip,
        protocol: location.protocol.replace(':', '').toUpperCase(),
        city: data.city,
        region: data.region_code,
        country: data.country_name,
        isp: data.org
      };

      return { lat: data.latitude, lon: data.longitude };
    } catch (e) {
      error = e.message;
      return null;
    } finally {
      loading = false;
    }
  }

  onMount(async () => {
    const L = await import('leaflet');

    const coords = await fetchIpInfo();
    const lat = coords?.lat ?? -6.2;
    const lon = coords?.lon ?? 106.8;

    const map = L.map(mapEl, {
      zoomControl: true,
      attributionControl: true
    }).setView([lat, lon], 11);

    L.tileLayer(
      'https://{s}.basemaps.cartocdn.com/light_all/{z}/{x}/{y}{r}.png',
      {
        maxZoom: 19,
        subdomains: 'abcd',
        attribution: 'shinraapi'
      }
    ).addTo(map);



    const icon = L.divIcon({
      className: 'relative',
      html: `
        <div class="absolute top-0 left-0 w-4 h-4 bg-red-500 rounded-full rounded-bl-none -rotate-45 ring-2 ring-white"></div>
        <div class="absolute -top-3.5 -left-2.5 w-10 h-10 bg-red-500/30 rounded-full animate-ping"></div>
      `,
      iconSize: [20, 20],
      iconAnchor: [10, 20]
    });

    L.marker([lat, lon], { icon }).addTo(map);
  });
</script>

<svelte:head>
  <link
    rel="stylesheet"
    href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
  />
</svelte:head>

<div class="w-full mx-auto rounded-xl overflow-hidden font-sans">
  <div class="h-[200px] w-full" bind:this={mapEl}></div>

  <div class="grid grid-cols-2 sm:grid-cols-4 gap-5 p-5">
    <div class="flex flex-col gap-1">
      <span class="text-[11px] tracking-wide text-neutral-500">IP ADDRESS</span>
      <span class="text-sm font-medium text-blue-400">{loading ? 'Memuat...' : ipData.ip}</span>
    </div>
    <div class="flex flex-col gap-1">
      <span class="text-[11px] tracking-wide text-neutral-500">PROTOKOL</span>
      <span class="text-sm font-medium text-sky-500">{ipData.protocol}</span>
    </div>
    <div class="flex flex-col gap-1">
      <span class="text-[11px] tracking-wide text-neutral-500">LOKASI ANDA</span>
      <span class="text-sm font-medium text-sky-500">{ipData.city}, {ipData.region}, {ipData.country}</span>
    </div>
    <div class="flex flex-col gap-1">
      <span class="text-[11px] tracking-wide text-neutral-500">ISP</span>
      <span class="text-sm font-medium text-sky-500">{ipData.isp}</span>
    </div>
  </div>

  {#if error}
    <p class="text-sm text-sky-400 px-6 pb-4">⚠ {error}</p>
  {/if}
</div>

<style>
  /* Ini elemen internal dari library leaflet, bukan markup kita sendiri,
     jadi nggak bisa kena Tailwind classes — tetep pakai CSS biasa + :global() */
  :global(.leaflet-control-attribution) {
    background: rgba(0, 0, 0, 0.6) !important;
    color: #999 !important;
  }

  :global(.leaflet-control-attribution a) {
    color: #60a5fa !important;
  }
</style>
