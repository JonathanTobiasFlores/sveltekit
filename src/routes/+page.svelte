<script>
    import Navbar from "$lib/components/Navbar.svelte";
    import Main from "$lib/components/Main.svelte";
    import Footer from "$lib/components/Footer.svelte";
    import BrowserMockup from "$lib/components/BrowserMockup.svelte";
</script>

<div class="min-h-screen flex flex-col">
    <header>
      <Navbar />
    </header>
  
    <main class="flex-1">
      <slot><BrowserMockup /></slot>
    </main>
  
    <footer class="footer footer-center p-10 bg-base-200 text-base-content rounded">
      <div class="grid grid-flow-col gap-4">
        <Footer />
      </div>
    </footer>
  </div>