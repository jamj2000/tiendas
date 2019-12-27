<script>
  import { Link } from "svelte-routing";

  function toggle() {
    this.textContent = this.textContent == "☰" ? "🗙" : "☰";

    // Sólo ES6+
    [...document.getElementsByClassName("item")].forEach(element =>
      element.classList.toggle("active")
    );
  }
</script>

<style>
  /* Basic styling */
  * {
    box-sizing: border-box;
  }

  nav {
    _background: lightblue;
    background: #fdebc9;
    padding: 8px;
  }

  ul {
    list-style-type: none;
  }

  /* .button a {
    padding: 7.5px 15px;
    background: palegreen;
    border: 1px mediumseagreen solid;
  }
  .logo a,
  .toggle a {
    font-size: 20px;
  } */
  
  .menu li:hover {
    text-shadow: 3px 3px 4px #6f6f70;
  }

  .menu li {
    font-weight: bold;
    font-size: 16px;
    padding: 15px 5px;
    white-space: nowrap;
  }


  /* Móvil */
  .menu {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: center;
  }
  .toggle {
    order: 1;
  }
  .item.button {
    order: 2;
  }
  .item {
    width: 100%;
    text-align: center;
    order: 3;
    display: none;
  }
  .active {
    display: block;
  }
  /* Tablet */
  @media all and (min-width: 600px) {
    .menu {
      justify-content: center;
    }
    .logo {
      flex: 1;
    }
    .toggle {
      flex: 1;
      text-align: right;
    }
    .item.button {
      width: auto;
      order: 1;
      display: block;
    }
    .toggle {
      order: 2;
    }
  }
  /* PC */
  @media all and (min-width: 900px) {
    .item {
      display: block;
      width: auto;
    }
    .toggle {
      display: none;
    }
    .logo {
      order: 0;
    }
    .item {
      order: 1;
    }
    .button {
      order: 2;
    }
    .menu li {
      padding: 15px 10px;
    }
    .menu li.button {
      padding-right: 0;
    }
  }
</style>

<nav>
  <ul class="menu">
    <li class="logo">
      <Link to="/">🛒 Inicio</Link>
    </li>
    <li class="item active">
      <Link to="/articulos">🎁 Artículos</Link>
    </li>
    <li class="item active">
      <Link to="/clientes">👥 Clientes</Link>
    </li>
    <li class="item active button">
      <Link to="/">Sign In</Link>
    </li>
    <li class="item active button secondary">
      <Link to="/">Sign Up</Link>
    </li>
    <li class="toggle">
      <Link on:click={toggle}>🗙</Link>
    </li>
  </ul>
</nav>
