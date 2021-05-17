<script>
    const LoremIpsum = require("lorem-ipsum").LoremIpsum;

    const lorem = new LoremIpsum({
        sentencesPerParagraph: {
            max: 8,
            min: 4,
        },
        wordsPerSentence: {
            max: 16,
            min: 4,
        },
    });

    let amountOfParagraphs = 'Amount of paragraphs';
    let inputWarning = '';
    const outputParagraphs = [];

    function generateLoremIpsum() {
        outputParagraphs.length = 0;
        const inputParsed = parseInt(amountOfParagraphs, 10);

        // If it isn't a number show a warning message.
        if (isNaN(inputParsed))
            return (inputWarning = 'Error, please fill in a Number in order to generate paragraphs.');
        // Reset warning message if it is a number.
        inputWarning = '';

        for (let i = 0; i < inputParsed; i++) {
            let generatedParagraph = lorem.generateParagraphs(1);
            outputParagraphs.push(generatedParagraph);
        }
        console.log(outputParagraphs);
    }
</script>

<style>
    input {
        width: 200px;
        margin: 10px;
        text-align: center;
        font-size: 15px;
        opacity: 80%;
    }

    .input-label {
        margin: 10px;
        opacity: 80%;
    }

    .alert {
        margin: 10px;
        opacity: 80%;
        color: red;
    }
</style>

<div>
    <div class="input-label">Enter the amount of Paragraphs you want in Lorem Ipsum format.</div>
    <input bind:value={amountOfParagraphs} on:change={() => generateLoremIpsum()} />

    <div class="alert">{inputWarning}</div>

    {#each outputParagraphs as outputParagraph}
        <p>{outputParagraph}</p>
    {/each}
</div>
