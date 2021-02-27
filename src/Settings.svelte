<script>
	export let diffHandler = () => {};
	export let catHandler = () => {};

	let currentDiff = 'e';
	let currentCat = 'g';
	const diffHandle = (selection) => {
		currentDiff = selection
		diffHandler(selection)
	}
	const catHandle = (selection) => {
		currentCat = selection
		catHandler(selection)
	}

</script>

<main>
	<div>
		<h2>Difficulty</h2>
		<button class="{currentDiff === 'e' ? 'selected' : ''}" on:click={() => {diffHandle('e')}}>
			Easy
		</button>
		<button class="{currentDiff === 'm' ? 'selected' : ''}" on:click={() => {diffHandle('m')}}>
			Medium
		</button>
		<button class="{currentDiff === 'h' ? 'selected' : ''}" on:click={() => {diffHandle('h')}}>
			Hard
		</button>
	</div>
	<div>
		<h2>Category</h2>
		<button class="{currentCat === 'g' ? 'selected' : ''}" on:click={() => {catHandle('g')}}>
			Geography
		</button>
		<button class="{currentCat === 'm' ? 'selected' : ''}" on:click={() => {catHandle('m')}}>
			Music
		</button>
		<button class="{currentCat === 'sp' ? 'selected' : ''}" on:click={() => {catHandle('sp')}}>
			Sports
		</button>
		<button class="{currentCat === 'f' ? 'selected' : ''}" on:click={() => {catHandle('f')}}>
			Film
		</button><br>
		<button class="{currentCat === 'p' ? 'selected' : ''}" on:click={() => {catHandle('p')}}>
			Politics
		</button>
		<button class="{currentCat === 'a' ? 'selected' : ''}" on:click={() => {catHandle('a')}}>
			Animals
		</button>
		<button class="{currentCat === 'sc' ? 'selected' : ''}" on:click={() => {catHandle('sc')}}>
			Science
		</button>
		<button class="{currentCat === 'h' ? 'selected' : ''}" on:click={() => {catHandle('h')}}>
			History
		</button>
	</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}
	button {
		width: 90px;
		height: 40px;
		border-radius: 20px;
		border: none;
		background-color: #999;
		color: #fff;
	}
	.selected {
		background-color: #0398fc;
	}
	h2 {
		color: #0398fc;
		text-transform: uppercase;
		font-size: 1.5em;
		font-weight: 100;
	}

	h1 {
		color: #0398fc;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>