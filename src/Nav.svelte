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
    background: lightblue;
    padding: 8px;
  }

  ul {
    list-style-type: none;
  }

  .button a {
    padding: 7.5px 15px;
    background: palegreen;
    border: 1px mediumseagreen solid;
  }

  .menu li:hover {
    text-shadow: -2px -2px 8px rgb(0, 0, 0);
    text-shadow: 2px 2px 6px rgb(0, 0, 0);
  }

  .menu li {
        font-weight: bold;
    font-size: 16px;
    padding: 15px 5px;
    white-space: nowrap;
  }
  .logo a,
  .toggle a {
    font-size: 20px;
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
  .item.active {
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
      <a href="/">Sign In</a>
    </li>
    <li class="item active button secondary">
      <a href="/">Sign Up</a>
    </li>
    <li class="toggle">
      <a href="/" on:click={toggle}>🗙</a>
    </li>
  </ul>
</nav>
