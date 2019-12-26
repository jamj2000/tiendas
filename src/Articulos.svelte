<script>
  import { onMount, beforeUpdate, afterUpdate, tick } from "svelte";

  import Form from "./Form.svelte";
  import Articulo from "./Articulo.svelte";
  import Boton from "./Boton.svelte";

  let url = `https://tiendaw.herokuapp.com/api/articulos`;
  let busqueda = "";

  onMount(async () => {
    const response = await fetch(url);
    jsonData = await response.json();
  });



  // this se refiere al formulario
  function handleSubmit() {
    busqueda = this.elements.buscar.value;
  }

  // this se refiere al input
  function handleKeyup() {
    busqueda = this.value;
  }

  function insertar(objeto) {
    if (Object.values(objeto).every(x => x !== null && x !== "")) {
      fetch(url, {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(objeto)
      })
        .then(res => res.json())
        .then(articulo => {
          console.log(articulo);
          jsonData = [...jsonData, articulo];
          OK.style.display = "block";
          setTimeout(() => (OK.style.display = "none"), 1500);
        })
        .catch(err => {
          KO.style.display = "block";
          setTimeout(() => (KO.style.display = "none"), 1500);
        });
    }
  }

  function modificar(id, objeto) {
    // let objeto = { nombre: campo1, precio: campo2 };

    fetch(`${url}/${id}`, {
      method: "PUT",
      headers: { "Content-Type": "application/json" },
      body: JSON.stringify(objeto)
    })
      .then(res => res.json())
      .then(articulo => {
        console.log(articulo);
        OK.style.display = "block";
        setTimeout(() => (OK.style.display = "none"), 1500);
      })
      .catch(err => {
        KO.style.display = "block";
        setTimeout(() => (KO.style.display = "none"), 1500);
      });
  }

  function eliminar(id) {
    // if (confirm("La información seleccionada va a ser eliminada. ¿Está seguro?")) {
    fetch(`${url}/${id}`, {
      method: "DELETE"
    })
      .then(res => res.json())
      .then(articulo => {
        console.log(articulo);
        jsonData = jsonData.filter(x => x._id !== articulo._id);
        OK.style.display = "block";
        setTimeout(() => (OK.style.display = "none"), 1500);
      })
      .catch(err => {
        KO.style.display = "block";
        setTimeout(() => (KO.style.display = "none"), 1500);
      });

    // }
  }

  let jsonData = [];

  $: regex = new RegExp(busqueda, "gi");
  $: data = busqueda
    ? jsonData.filter(element => regex.test(element.nombre))
    : jsonData;


</script>

<style>
  .container {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: left;
    flex-wrap: wrap;
  }

  .botones {
    text-align: right;
  }
</style>

<h1>ARTÍCULOS</h1>
<Form {handleSubmit} {handleKeyup} />

<div class="container">
  <Articulo let:articulo>
    <div slot="botones" class="botones">
      <Boton class="btn btn-insertar" on:click={() => insertar(articulo)}>
        <span>✏️</span>
      </Boton>
    </div>
  </Articulo>
</div>

<div class="container">
  {#each data as articulo}
    <Articulo {articulo}>
      <div slot="botones" class="botones">
        <Boton class="btn btn-modificar"  on:click={() => modificar(articulo._id, articulo)}>
          <span>📝</span>
        </Boton>
        <Boton class="btn btn-eliminar" on:click={() => eliminar(articulo._id)}>
          <span>❌</span>
        </Boton>
      </div>
    </Articulo>
  {/each}
</div>
