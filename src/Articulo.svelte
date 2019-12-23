<script>
  import Boton from "./Boton.svelte";
  export let articulo = {};
</script>

<div>
  {articulo.nombre} {articulo.precio} €
  <Boton class="btn btn-modificar">
    <span>📝</span>
  </Boton>
  <Boton class="btn btn-eliminar">
    <span>❌</span>
  </Boton>
</div>
