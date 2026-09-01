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

<Router {routes} />
