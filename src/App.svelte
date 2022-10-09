<script>
  let apiUrl = "https://sensitive-plot-production.up.railway.app/";
  import Fa from "svelte-fa";
  import { faSearch } from "@fortawesome/free-solid-svg-icons";
  let searchedWord = "卵";
  let searchedSomething = false;

  async function searchWord() {
    searchedSomething = true;
    const response = await fetch(`${apiUrl}${searchedWord}`);
    const words = await response.json();
    if (response.ok) {
      return await words;
    }
  }
</script>

<main>
  <h1>Japanese Dictionary</h1>
  <section>
    <input
      bind:value={searchedWord}
      type="text"
      placeholder="Enter word to look up"
    />
    <div id="fa-search" on:click={searchWord}>
      <Fa icon={faSearch} />
    </div>
  </section>

  {#if !searchedSomething}
    <p>Hi there! This is a Japanese-to-Japanese dictionary app.</p>
    <p>You can use either Hiragana, Katakana or Kanji to look up a word.</p>
  {:else}
    {#await searchWord()}
      <p>Getting those words for you...</p>
    {:then wordList}
      {#each wordList as word}
        <p>{word.word}</p>
      {/each}
    {/await}
  {/if}
</main>

<style>
  main {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  section {
    display: flex;
    align-items: center;
    justify-content: center;
  }
  #fa-search {
    margin-left: 1em;
    background-color: rgb(0, 255, 255, 0);
    padding: 1em;
    transition: background 0.25s ease-in;
    border-radius: 0.25em;
  }

  #fa-search:hover {
    background-color: rgb(0, 255, 255, 0.5);
  }
  input {
    height: 3em;
    width: 23em;
    border-width: 0;
    border-bottom: 5px solid lightgray;
    border-radius: 0;
    transition: border 0.2s ease;
    font-size: 5;
  }
  input:focus {
    border-bottom: 5px solid #4fbfff;
    outline: none;
  }
  input[type="text" i] {
    padding-left: 1em;
  }
</style>
