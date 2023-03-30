<script>
	import { onMount } from 'svelte';
	import { tweened } from 'svelte/motion';
	import { fade } from 'svelte/transition';
	import { cubicOut } from 'svelte/easing';

	let showDescription = false;

	const scoreVal = tweened(0, {
		duration: 2000,
		easing: cubicOut
	});

	onMount(() => {
		showDescription = true;
		setTimeout(() => {
			scoreVal.set(76);
		}, 1500);
	});
</script>

<div class="overall-score rounded-b-[2rem] lg:rounded-[2rem] lg:flex-1 gap-4 lg:gap-8">
	<h5 class="lg:text-xl">Your Result</h5>
	<div class="score p-6 lg:p-12">
		<strong class="text-5xl lg:text-7xl">{Math.floor($scoreVal)}</strong>
		<span>of 100</span>
	</div>
	<div class="score-description flex opacity-0">
		<h3 class="text-2xl lg:text-3xl">Great</h3>
		<p class="text-sm lg:text-base">
			You scored higher than 65% of the people who have taken these tests.
		</p>
	</div>
</div>

<style lang="scss">
	.overall-score {
		padding: 1rem 3rem 2rem;
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		text-align: center;
		background-image: linear-gradient(
			180deg,
			var(--gradient-light-slate-blue-background) 0%,
			var(--gradient-light-royal-blue-background) 100%
		);

		h5,
		p {
			color: var(--neutral-light-lavender);
		}

		h3,
		strong {
			color: var(--neutral-white);
		}

		span {
			color: var(--neutral-light-lavender);
			opacity: 0.5;
		}

		.score {
			background-image: linear-gradient(
				180deg,
				var(--gradient-violet-blue-circle) 0%,
				var(--gradient-persian-blue-circle) 100%
			);

			display: flex;
			flex-direction: column;
			border-radius: 100%;
			aspect-ratio: 1/1;
			width: fit-content;
			align-items: center;
			justify-content: center;
			strong {
				line-height: 1;
				font-weight: 800;
			}
		}

		.score-description {
			flex-direction: column;
			gap: 0.5rem;
            animation: fadeIn 500ms forwards 3.75s ease-in-out;
			h3 {
				font-weight: 700;
			}
			p {
				line-height: 1.35;
			}
		}

        // Create keyframe that animates the score-description opacity from 0 to 1 after 2.5 second delay over 500ms
        @keyframes fadeIn {
            0% {
                opacity: 0;
            }
            100% {
                opacity: 1;
            }
        }

	}
</style>
