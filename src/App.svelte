<script>
	export let game = false;
	export let loading = false;
	export let difficulty = 'e';
	export let category = 'g';
	const setDifficulty = (val) => {
		difficulty = val
	}
	const setCategory = (val) => {
		category = val
	}


	const diffArr = ['e', 'm', 'h']
    const catArr = ['g', 'm', 'sp', 'f', 'p', 'a', 'sc', 'h']
    const catKeys = ['22', '12', '21', '11', '24', '27', '17', '23']
    const diffKeys = ['easy', 'medium', 'hard']
    let questions = []

    const getQ = () => {
		difficulty = diffKeys[diffArr.indexOf(difficulty)]
    	category = catKeys[catArr.indexOf(category)]

		console.log('Initial call: ', difficulty, category)

        let url = 'https://opentdb.com/api.php?amount=10&category=' + category + '&difficulty=' + difficulty + '&type=multiple'

        fetch(url).then((resp) => resp.json().then((data) => {questions.push(data.results)}))
		console.log(questions)
    }

	const startGame = () => {
		loading = true
		getQ()
		setTimeout(() => { 
			loading = false; 
			game = !game
		}, 1500)
	}

	const reset = () => {
		game = !game
		questions = []
		difficulty = 'e';
		category = 'g';
	}


	import Settings from './Settings.svelte';
	import Trivia from './Trivia.svelte';
</script>

<main>
	<h1>Trivia Challenge!</h1>
	{#if !game}
	<Settings 
		diffHandler={setDifficulty}
		catHandler={setCategory}
	/>
	<br>
	<button on:click={startGame}>START</button>
	{#if loading}
	<div class="loading">
		<h1>Loading...</h1>
	</div>
	{/if}
	{:else}
	<Trivia questions={questions[0]} reset={reset} />
	{/if}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}
	button {
		width: 80px;
		height: 40px;
		border-radius: 20px;
		border: none;
		background-color: #0398fc;
		color: #fff;
	}
	.loading {
		width: 100vw;
		height: 100vh;
		background-color: rgba(255, 255, 255, 0.9);
		position: absolute;
		padding-top: 15%;
		top: 0;
		left: 0;
	}
	h1 {
		color: #0398fc;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
		margin-bottom: 10px;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>