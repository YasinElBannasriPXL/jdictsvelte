<script>
import WordList from "./lib/WordList.svelte";
import Menu from "./lib/Menu.svelte";
import logo from "./assets/Frame.svg";
import {
    faSearch
} from "@fortawesome/free-solid-svg-icons";
import Fa from "svelte-fa";

let apiUrl = "https://sensitive-plot-production.up.railway.app/";
let searchedWord = "";
let searchedSomething = false;
let promise;

if (searchedWord) promise = searchWord();

async function searchWord() {
    searchedSomething = true;
    const response = await fetch(`${apiUrl}${searchedWord}`);
    const words = await response.json();
    console.log(words);
    if (response.ok) {
        return await words;
    }
}
</script>

<main>
    <Menu />
    <div id="branding">
        <img src={logo} alt="site logo" />
        <h1>Japanese Dictionary</h1>
    </div>
    <section id='input'>
        <form
            on:submit|preventDefault={() => {
            promise = searchWord();
            }}
            >
            <input
                bind:value={searchedWord}
                type="text"
                placeholder="Enter word to look up"
                />
            <div
                id="fa-search"
                on:click={() => {
                promise = searchWord();
                }}
                >
                <Fa icon={faSearch} />
            </div>
        </form>
    </section>

    <section id="words-section">
        {#if !searchedSomething}
        <p>Hi there! This is a Japanese-to-Japanese dictionary app.</p>
        <p>You can use either Hiragana, Katakana or Kanji to look up a word.</p>
        {:else}
        {#await promise}
        <div id="loading-bar-wrapper">
            <div id="loading-bar" />
        </div>
        <p>Getting those words for you...</p>
        {:then wordList}
        {#each wordList as word}
        <WordList {...word} />
        {/each}
        {/await}
        {/if}
    </section>
</main>

<style>

    #input {
        max-width: 95vw;
        overflow: hidden;
    }
#branding {
    display: flex;
    align-items: center;
    justify-content: flex-start;
    padding-bottom: 2em;
}

#branding h1 {
    margin-right: auto;
    margin-left: 0.2em;
}

main {
    z-index: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
}

main img {
    margin-top: 0.5em;
    aspect-ratio: 1;
    width: 5em;
    align-self: center;
}

section {
    display: flex;
    align-items: center;
    justify-content: center;
}

form {
    display: flex;
    max-width: 100vw;
    justify-content: space-around;
}

#words-section {
    display: flex;
    align-items: center;
    flex-direction: column;
    gap: 0.6em;
}

#loading-bar-wrapper {
    border-radius: 1em;
    width: 200px;
    height: 1em;
    background-color: gray;
}

#loading-bar {
    height: 100%;
    width: 10%;
    background-color: #4fbfff;
    animation: left-to-right 0.25s alternate infinite ease-in forwards;
}

@keyframes left-to-right {
    from {
        width: 0%;
    }

    to {
        width: 100%;
    }
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
    margin-left: 1.4em;
    height: 3em;
    width: 80vw;
    max-width: 40em;
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

input[type="text"i] {
    padding-left: 1em;
}
</style>
