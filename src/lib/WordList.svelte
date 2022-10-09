<script>
    export let hiraganaReading;
    export let word;
    export let definition;
    export let someNumber;
</script>


<div id="wrapper">
    <div id="word">
        <div id="word-reading">{hiraganaReading}</div>
        <div id="actual-word">{word}</div>
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
        max-width: 75em;
        background-color: #1A1B21;
        border: 1px solid #dcdcdc11;
        border-radius: 2px;

    }
    #wrapper:nth-child(1) {
        margin-top: 2.5em;
    }
    #word {
        margin-top: 1em;
        margin-bottom: 1em;
    }
    #actual-word {
        background-color: #161619;
        padding: 0.7em;
        margin-left: 2em;
        border-radius: 5px;
        width: max-content;
        font-size: 1.5rem;
        font-weight: 600;
    }
    #word-reading {
        padding-left: 3.4em;
    }
    
    #definition {
        padding: 0.3em;
        padding-left: 3em;
    }
</style>