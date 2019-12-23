<script>
  import { Link } from "svelte-routing";
</script>

<style>
nav {
    padding: 1em;
    display: flex;
    flex-direction:  row;

}


 ul {
    list-style: none;
    display: flex;    
    justify-content: flex-end;
}

nav > ul > li {
  color: white;
  display: block;
  text-decoration: none;
  padding: .5em 1em;
}
</style>


<nav>
  <Link to="/"><span>Inicio</span></Link>
  <ul style="padding-left: 50px">
    <li>
      <Link to="/articulos">Artículos</Link>
    </li>
    <li>
      <Link to="/clientes">Clientes</Link>
    </li>
  </ul>
</nav>
