<script>
  import Router from 'svelte-spa-router';
  import Navbar from './components/navbar.svelte';
  import Home from './pages/Home.svelte';
  import Docs from './pages/Docs.svelte';

  const routes = {
    '/': Home,
    '/docs': Docs
  };
</script>
<svelte:head>
  <title>Shinra API — Free API untuk Developer</title>

  <meta
    name="description"
    content="Shinra API adalah API gratis untuk developer Indonesia tanpa API key, tanpa paywall, dan mudah digunakan."
  />

  <meta
    name="keywords"
    content="Shinra API, API gratis, free API Indonesia, API developer, REST API, rest api gratis, free rest api"
  />

  <meta name="robots" content="index, follow" />
</svelte:head>
<Router {routes} />
