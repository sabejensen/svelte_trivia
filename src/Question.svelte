<script>
	export let question;
    export let correct;
    export let incorrect;
    export let countHandler = () => {};
	export let scoreHandler = () => {};

    let answers = incorrect;
    let index = Math.floor(Math.random() * Math.floor(4))
    answers.splice(index, 0, correct)
    
    const select = (pick) => {
        if(pick == correct) {
            scoreHandler()
        }
        countHandler()
    }
</script>

<main>
	<p>{question}</p>
    <button on:click={() => {select(answers[0])}}>{answers[0]}</button>
    <button on:click={() => {select(answers[1])}}>{answers[1]}</button>
    <button on:click={() => {select(answers[2])}}>{answers[2]}</button>
    <button on:click={() => {select(answers[3])}}>{answers[3]}</button>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}
	button {
		width: 80%;
		height: 40px;
		border-radius: 20px;
		border: none;
		background-color: #0398fc;
		color: #fff;
	}

	h2 {
		color: #0398fc;
		text-transform: uppercase;
		font-size: 1.5em;
		font-weight: 100;
		margin-bottom: 10px;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>