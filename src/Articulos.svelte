<script>
  import Fetch from "./Fetch.svelte";
  import Form from "./Form.svelte";
  import Articulo from "./Articulo.svelte";
  import Boton from "./Boton.svelte";

  let busqueda = "";
  // this se refiere al formulario
  let handleSubmit = () => (busqueda = this.elements.buscar.value);

  // this se refiere al input
  let leer = () => (busqueda = this.value);
</script>



<h1>ARTÍCULOS</h1>
<Form {handleSubmit}  {leer} />

<Fetch contenido="articulos" let:data>

  <Boton class="btn btn-insertar">
    <span>✏️</span>
  </Boton>

  {#each data as articulo}
    <Articulo {articulo} />
  {/each}

</Fetch>
