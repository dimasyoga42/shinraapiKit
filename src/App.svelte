<script>
  import Navbar from "./components/navbar.svelte"
  import Ipcardinfo from "./components/ipcardinfo.svelte"
  import Footer from "./components/footer.svelte"
  import About from "./components/about.svelte"
</script>

<div class="flex max-w-7xl m-auto w-full justify-center mx-auto">
  <div>
    <Navbar />
    <Ipcardinfo />
    <About />
  </div>
  <Footer />
</div>
