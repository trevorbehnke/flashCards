<script>
	export let task;
	export let shortcut;
	export let showCardBack;
</script>

<div class="flip-box-front rounded-lg border-2 border-black shadow-xl">
	<div id="image-cont">
		<p class=" text-3xl">{task}</p>
	</div>
</div>

<div
	class="flip-box-back rounded-lg border-2 border-black shadow-xl"
	class:conceal-answer={showCardBack}
>
	<p class="text-3xl">{shortcut}</p>
</div>

<style>
	/* Position the front and back side */
	.flip-box-front,
	.flip-box-back {
		position: absolute;
		width: 100%;
		height: 100%;

		backface-visibility: hidden;
		/* box-shadow: -1px 1px 3px black; */
	}

	/* Style the front side */
	.flip-box-front {
		background-color: #ddd;
		color: black;
		display: flex;
		justify-content: center;
	}

	@keyframes revealTextSlowly {
		to {
			color: white;
		}
	}

	.conceal-answer {
		animation: revealTextSlowly 0.3s forwards;
	}

	/* Style the back side */
	.flip-box-back {
		display: flex;
		justify-content: center;
		align-items: center;
		background-color: #61592f;
		color: #61592f;
		/* 		color: white; */
		font-size: 1.3rem;
		transform: rotateY(180deg);
	}

	#image-cont {
		/* background-color: hsl(50, 65%, 75%); */
		max-width: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	/* img {
		max-height: 80%;
	} */
</style>
