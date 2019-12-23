<script>
  import { onMount } from "svelte";

  export let contenido = '';
  export let url = `https://tiendaw.herokuapp.com/api/${contenido}`;
  export let searchTerm = undefined;



  let jsonResponse = [];

  $: regex = new RegExp(searchTerm, "gi");
  $: data = searchTerm
    ? jsonResponse.filter(element => regex.test(element.nombre))
    : jsonResponse;

  onMount(async () => {
    const response = await fetch(url);
    jsonResponse   = await response.json();
  });
</script>

<slot {data} />
