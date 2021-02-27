<script>
	export let questions;
    export let reset = () => {};

    for(let i = 0; i < questions.length; i++) {
        questions[i].type = i;
    }

    let count = 0
    let score = 0
    let x = 0

    const countHandler = () => {
        count++;
    }
    const scoreHandler = () => {
        score++;
    }

    
    import Question from './Question.svelte'
</script>

<main>
    {#if count < 10}
	<h2>{questions[0].category} - {questions[0].difficulty} - {score}/10</h2>
    {:else}
    <h1>Final Score: {score}/10</h1><br>
    <button on:click={reset}>Retry</button>
    {/if}
    {#each questions as q}
        {#if q.type == count}
        <Question question={q.question} correct={q.correct_answer} incorrect={q.incorrect_answers} countHandler={countHandler} scoreHandler={scoreHandler} />
        {/if}
    {/each}
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

	h2, h1 {
		color: #0398fc;
		text-transform: uppercase;
		font-size: 1.5em;
		font-weight: 100;
		margin-bottom: 10px;
	}
    h1 {
        font-size: 2.5em;
    }

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>