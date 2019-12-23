<script>
  import { Route } from "svelte-routing";
  import Articulos from "./Articulos.svelte";
  import Clientes from "./Clientes.svelte";

</script>

<div>
  <Route path="/articulos" component={Articulos} />
  <Route path="/clientes" component={Clientes} />
</div>
