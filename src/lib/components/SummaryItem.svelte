<script>
	import { onMount } from "svelte";
    import { tweened } from 'svelte/motion';
	import { cubicOut } from 'svelte/easing';


	// Add an image, title, score, color, and backgroundColor prop
	export let image;
	export let title;
	export let score = 0;
	export let color = 'black';
    export let delay = 0;
	let backgroundColor = `rgba(${color}, 0.1)`;

    const scoreVal = tweened(0, {
        duration: 1000,
        easing: cubicOut
    });

    onMount(() => {
        setTimeout(() => {
            scoreVal.set(score)
        }, delay);
    });
</script>

<div
	class="summary-item flex px-4 py-4 gap-2 items-center justify-center rounded-xl text-sm"
	style="background-color: {backgroundColor};"
>
	<!-- Add an image tag with the image prop -->
	{#if image}
		<img src={image} alt={title} />
	{/if}
	<!-- Add a title and score -->
	<h3 class="flex-1 font-bold tracking-wider" style="color: rgb({color})">{title}</h3>
	<div class="score flex items-center justify-center leading-none gap-2">
		<strong>{Math.round($scoreVal)}</strong>
		<span class="text-neutral-400">/ 100</span>
	</div>
</div>
