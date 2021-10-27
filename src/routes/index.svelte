<script>
	import Tabs from '$lib/components/Tabs.svelte';

	import { shortcuts } from '../data.js';

	import Flashcard from '$lib/components/Flashcard.svelte';

	let flashcardIndex = 0;
	$: task = shortcuts[flashcardIndex].task;
	$: shortcut = shortcuts[flashcardIndex].shortcut;

	let showCardBack = false;
	const toggleShowBack = () => (showCardBack = !showCardBack);

	const prevCard = () => {
		showCardBack = false;
		if (flashcardIndex === 0) {
			flashcardIndex = shortcuts.length - 1;
		} else {
			flashcardIndex -= 1;
		}
	};

	const nextCard = () => {
		showCardBack = false;
		if (flashcardIndex === shortcuts.length - 1) {
			flashcardIndex = 0;
		} else {
			flashcardIndex += 1;
		}
	};

	// tabs
	let items = ['Mac', 'Windows'];
	let activeItem = 'Mac';
	const tabChange = (e) => (activeItem = e.detail);
</script>

<main class="">
	<Tabs {activeItem} {items} on:tabChange={tabChange} />
	{#if activeItem === 'Mac'}
		<!-- FLASHCARD -->
		<div class="flip-box">
			<div class="flip-box-inner" class:flip-it={showCardBack}>
				<Flashcard {task} {shortcut} {showCardBack} />
			</div>
		</div>

		<!-- BUTTONS -->
		<div id="btn-cont" class="rounded-lg pt-4 flex justify-evenly w-96">
			<button class="rounded-lg w-20 p-2" on:click={prevCard}>&#8592;</button>

			<button class="rounded-lg p-2 w-32" on:click={toggleShowBack}>
				{showCardBack ? 'Hide Answer' : 'Show Answer'}
			</button>

			<button class="rounded-lg w-20 p-2" on:click={nextCard}>&#8594;</button>
		</div>
	{:else if activeItem === 'Windows'}
		Add this!
	{/if}
</main>

<style>
	main {
		display: flex;
		flex-direction: column;
		align-items: center;
		margin-top: 15%;
		/* height: 100vh; */
	}

	/* The flip box container - set the width and height to whatever you want. We have added the border property to demonstrate that the flip itself goes out of the box on hover (remove perspective if you don't want the 3D effect */
	.flip-box {
		/* background-color: transparent; */
		width: 350px;
		height: 250px;
		/* 		border: 1px solid #ddd; */
		perspective: 1000px; /* Remove this if you don't want the 3D effect */
	}

	/* This container is needed to position the front and back side */
	.flip-box-inner {
		position: relative;
		width: 100%;
		height: 100%;
		text-align: center;
		transition: transform 0.4s;
		transform-style: preserve-3d;
	}

	/* Do an horizontal flip on button click */
	.flip-it {
		transform: rotateY(180deg);
	}

	#btn-cont {
		/* width: 300px; */
		/* padding: 10px 0; */
		/* display: flex; */
		/* justify-content: space-between; */
	}

	button {
		/* background-color: hsl(167, 63%, 45%); */
		/* padding: 10px 10px; */
		/* color: white; */
		background: rgba(255, 255, 255, 0.25);
		box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
		backdrop-filter: blur(4px);
		-webkit-backdrop-filter: blur(4px);
		border-radius: 10px;
		border: 1px solid rgba(255, 255, 255, 0.18);
		cursor: pointer;
	}

	button:hover {
		background: rgba(255, 255, 255, 0.4);
	}

	button:active {
		background-color: hsl(167, 63%, 45%);
	}
</style>
