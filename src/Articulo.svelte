<script>
  import Boton from "./Boton.svelte";
  export let articulo = {};
</script>

<style>
  .title {
    font-weight: bold;
  }
  .card {
    background-color: #fdebc9;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
    border-radius: 5px;
    transition: 0.3s;
    padding: 10px;
    margin: 10px;
   /*  width: 380px;
    min-width: 380px; 
    max-width: 400px; */
  }

  .card:hover {
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.4);
  }

  input {
    background-color: inherit;
    padding: 10px;
    font-size: 14px;
    color: black;
    border: 0;
    outline: none;
    margin-left: 5px;
    margin-bottom: 4px;
  }

  input[type="number"] {
    text-align: right;
    width: 100px;
  }
  input:focus {
    background-color: wheat;
  }

  input:required:invalid,
  input:focus:invalid {
    background-color: lightpink;
  }
</style>

<div class="card" on:click>

  <!-- <p>{articulo._id}</p> -->
  <input bind:value={articulo.nombre} class="title" />
  <input
    type="number"
    min="0"
    max="9999.99"
    step=".01"
    dir="rtl"
    bind:value={articulo.precio} />
  €
  <slot name="botones" />
  <slot {articulo} />
</div>
