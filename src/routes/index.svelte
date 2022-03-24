<script>
	import '@fontsource/outfit/900.css';
	import Scrolly from '$lib/components/Scrolly.svelte';
	import TTTwinkle from '$lib/components/TTTwinkle.svelte';

	let value;
	const steps = ['<p>This site is... </p>', '<p>... under construction.</p>', '<p>Nothing to see here, yet.</p>'];
</script>

<svelte:head>
	<title>Sebastian Lammers | Under Construction</title>
</svelte:head>

<section>
	<div class="hero">
		<h1>Psst, let me tell you a secret:</h1>
	</div>

	<div class="section-container">
		<div class="steps-container">
			<Scrolly bind:value>
				{#each steps as text, i}
					<div class="step" class:active={value === i}>
						<div class="step-content">{@html text}</div>
					</div>
				{/each}
				<div class="spacer" />
			</Scrolly>
		</div>
		<div class="sticky">
			<TTTwinkle />
		</div>
	</div>
	<div class="hero">
		<h1>Thanks for stopping by though!</h1>
	</div>
</section>

<style>
	section {
		font-family: 'Outfit', sans-serif;
	}

	:global(body) {
		overflow-x: hidden;
	}

	.hero {
		height: 90vh;
		display: flex;
		place-items: center;
		flex-direction: column;
		justify-content: center;
		text-align: center;
	}

	.hero h1 {
		font-size: 2.7rem;
	}

	.spacer {
		height: 40vh;
	}

	.sticky {
		position: sticky;
		top: 10%;
		flex: 1 1 60%;
		width: 60%;
	}

	.section-container {
		margin-top: 1em;
		text-align: center;
		transition: background 100ms;
		display: flex;
	}

	.step {
		height: 80vh;
		display: flex;
		place-items: center;
		justify-content: center;
	}

	.step-content {
		font-size: 2rem;
		background: whitesmoke;
		color: #ccc;
		border-radius: 5px;
		padding: 0.5rem 1rem;
		display: flex;
		flex-direction: column;
		justify-content: center;
		transition: background 500ms ease;
		box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.2);
		text-align: left;
		width: 75%;
		margin: auto;
		max-width: 500px;
	}

	.step.active .step-content {
		background: white;
		color: black;
	}

	.steps-container,
	.sticky {
		height: 100%;
	}

	.steps-container {
		flex: 1 1 40%;
		z-index: 10;
	}

	/* Comment out the following line to always make it 'text-on-top' */
	@media screen and (max-width: 768px) {
		.section-container {
			flex-direction: column-reverse;
		}
		.sticky {
			width: 95%;
			margin: auto;
		}
	}
</style>
