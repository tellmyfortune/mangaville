<script>
  import Nav from "./components/Nav.svelte";
  import Home from "./lib/Home.svelte";
</script>

<main>
  <Nav />
  <div class="flex flex-col items-center overflow-y-auto">
    <Home />
  </div>
  <br>
  <br>
</main>

<style global lang="postcss">
  @tailwind base;
  @tailwind components;
  @tailwind utilities;
</style>