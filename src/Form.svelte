<script>
  export let busqueda = undefined;
  export let handleSubmit = (event) => { };
  export let leer         = (event) => { };

  // let busqueda = "";
  // // this se refiere al formulario
  // let handleSubmit = () => (busqueda = this.elements.buscar.value);

  // // this se refiere al input
  // let leer = () => (busqueda = this.value);
</script>

<form on:submit|preventDefault={handleSubmit}>
  <label for="buscar">Buscar:</label>
  <input on:keyup={leer} type="search" id="buscar" required />
  <button type="submit">Buscar</button>
</form>
<!-- p> {busqueda} </p  -->
