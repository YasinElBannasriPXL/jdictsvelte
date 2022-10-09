<script>
  export let hiraganaReading;
  export let word;
  export let definition;
  export let someNumber;
  let visible = false;

  function addWord() {
    alert(someNumber);
  }
</script>

<div id="wrapper">
  <div id="word">
    <div id="word-reading">{hiraganaReading}</div>
    <div id="actual-word-wrapper" on:click={() => (visible = !visible)}>
      <div id="actual-word">{word}</div>
      {#if visible}
        <div id="word-menu">
          <ul>
            <li class="menu-item" on:click={addWord}>Add Word</li>
          </ul>
        </div>
      {/if}
    </div>
  </div>
  <div id="definition">
    <span>{definition}</span>
  </div>
</div>

<style>
  #wrapper {
    display: grid;
    grid-template-columns: 1fr;
    width: 95vw;
    max-width: 55em;
    background-color: #1a1b21;
    border: 1px solid #dcdcdc11;
    border-radius: 2px;
  }
  #wrapper:nth-child(1) {
    margin-top: 2.5em;
  }

  #word-menu {
    text-align: center;
    position: absolute;
    height: 100px;
    top: 2.6em;
    left: 0.2em;
    border-radius: 0.5em;
    width: 5em;
    background-color: #161619;
    z-index: 2;
    opacity: 0.8;
  }
  ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
  }
  .menu-item {
    font-size: 0.75rem;
  }
  .menu-item:hover {
    font-size: 0.75rem;
    background-color: #797979;
  }
  #word {
    margin-top: 2em;
    margin-bottom: 1em;
  }
  #actual-word-wrapper {
    position: relative;
    background-color: #161619;
    padding: 0.7em;
    margin-left: 2em;
    border-radius: 5px;
    width: max-content;
    font-size: 1.5rem;
    font-weight: 600;
  }
  #actual-word-wrapper:hover {
    background-color: #797979;
    cursor: pointer;
  }
  #word-reading {
    padding-left: 3.4em;
  }

  #definition {
    position: relative;
    padding: 0.3em;
    padding-left: 7em;
    padding-right: 7em;
    margin-bottom: 2em;
  }
  #definition:before {
    position: absolute;
    content: "";
    background-color: #4fbfff;
    left: 6em;
    border-radius: 1em;
    top: 0.3;
    width: 0.3em;
    height: 1.2em;
    opacity: 1;
  }
  @media screen and (max-width: 420px) {
    #definition {
      padding-right: 2em;
    }
  }
</style>
