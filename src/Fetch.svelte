<script>
  import { onMount } from "svelte";

  export let url = "https://academy.valentinog.com/api/link/";
  export let searchTerm = undefined;

  let jsonResponse = [];
  //let data = [];

  $: regex = new RegExp(searchTerm, "gi");
  $: data = searchTerm
    ? jsonResponse.filter(element => element.title.match(regex))
    : jsonResponse;

  onMount(async function() {
    const response = await fetch(url);
    const json = await response.json();
    jsonResponse = json;
    //data = json;
  });
</script>

<slot {data} />
