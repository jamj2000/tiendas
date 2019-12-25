<script>
  import Nav from "./Nav.svelte";
  import Contenido from "./Contenido.svelte";
  import { Router } from "svelte-routing";
</script>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
  }

  :global(*) {
    margin: 0;
    padding: 0;
  }

  :global(a:hover) {
    text-decoration: none;
    cursor: pointer;
  }
</style>

<Router>
  <Nav />
  <Contenido />
</Router>
