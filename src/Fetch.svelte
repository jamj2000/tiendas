<script>
  import { onMount } from "svelte";

  export let contenido = '';
  export let url = `https://tiendaw.herokuapp.com/api/${contenido}`;
  export let busqueda = undefined;



  let jsonResponse = [];

  $: regex = new RegExp(busqueda, "gi");
  $: data = busqueda
    ? jsonResponse.filter(element => regex.test(element.nombre))
    : jsonResponse;

  onMount(async () => {
    const response = await fetch(url);
    jsonResponse   = await response.json();
  });
</script>

<slot {data} />
