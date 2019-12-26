<script>
  import { Route } from "svelte-routing";
  import Articulos from "./Articulos.svelte";
  import Clientes from "./Clientes.svelte";
</script>

<style>
  main {
    padding: 20px;
  }
</style>

<main>
  <Route path="/articulos" component={Articulos} />
  <Route path="/clientes" component={Clientes} />

</main>
