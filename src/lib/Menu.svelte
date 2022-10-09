<script>
  import Fa from "svelte-fa";
  import { faBars } from "@fortawesome/free-solid-svg-icons";

  let menuShown = false;
</script>

<nav>
  <div
    tabindex="0"
    id="toggle-button"
    on:click={() => {
      menuShown = !menuShown;
    }}
  >
    <Fa icon={faBars} />
  </div>
  {#if menuShown}
    <div id="menu">
      <ul>
        <a href=""><li>My List</li></a>
        <a href=""><li>Account</li></a>
      </ul>
    </div>
  {/if}
</nav>

<style>
  nav {
    position: absolute;
    right: 0;
    top: 1em;
  }
  #toggle-button {
    cursor: pointer;
    font-size: 2em;
    padding: 0.3em;
    border-radius: 0.15em;
    position: absolute;
    justify-content: center;
    top: 3px;
    right: 3px;
    z-index: 6;
  }
  #toggle-button:hover {
    background: #2c2e31;
  }
  #toggle-button:focus {
    background: #2c2e31;
    box-shadow: 0 0 0 2px #4fbfff;
  }
  #menu {
    z-index: 4;
    background: #2c2e31;
    position: absolute;
    top: -1em;
    right: 0;
    width: 4em;
    min-height: 100vh;
    min-width: 12em;
    filter: drop-shadow(0em 0em 1em rgba(0,0,0,0.25))
  }

  #menu ul {
    display: flex;
    align-items: flex-start;
    justify-content: center;
    flex-direction: column;
    height: 20em;
    padding-left: 1em;
    padding: 0;
    gap: 1.5em;
    font-size: 1.50rem;
  }

  ul a {
    display: flex;
    align-items: center;
    vertical-align: center;
    width: 100%;
    height: 1em;
    padding-left: 1.25em;
    color: lightgray;
  }

  ul {
    display: flex;
    min-width: 9em;
    margin: 0;
    list-style-type: none;
  }
</style>
