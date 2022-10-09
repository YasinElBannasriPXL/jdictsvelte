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
        max-width: 50em;
        background-color: #1A1B21;
        border: 1px solid #dcdcdc11;
        border-radius: 2px;

    }
    #wrapper:nth-child(1) {
        margin-top: 2.5em;
    }
    #word {
        margin-top: 2em;
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
        position: relative;
        padding: 0.3em;
        padding-left: 7em;
        padding-right: 7em;
        margin-bottom: 2em;
    }
    #definition:before {
        position: absolute;
        content: '';
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