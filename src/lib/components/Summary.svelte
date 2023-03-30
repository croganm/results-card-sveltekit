<script>
	import SummaryItem from './SummaryItem.svelte';

    import data from "$lib/data.json";
    
    const summaryImages = import.meta.glob('$lib/assets/images/*.svg', {as: 'url', eager: true});
</script>

<div class="summary-container px-6 mt-6 flex flex-col gap-6 lg:flex-1 lg:py-8">

    <h3 class="font-bold">Summary</h3>
    <div class="summary-items">
        {#each data as item, i}
            <SummaryItem
                image={summaryImages[item.icon]}
                title={item.category}
                score={item.score}
                color={item.color}
                delay={250+(i*250)}
            />
        {/each}
        <!-- <SummaryItem
            image="$lib/assets/images/icon-reaction.svg"
            title="Reaction"
            score="80"
            color="var(--primary-light-red)"
        /> -->
    </div>
    <button class="btn btn-primary rounded-full">Continue</button>
</div>

<style lang="scss">
	.summary-items {
		display: flex;
		flex-direction: column;
		gap: 1.25rem;
	}

	button {
		color: white;
		background: var(--neutral-dark-gray-blue);
        padding: 1rem;

		&:hover {
			background: linear-gradient(
			180deg,
			var(--gradient-light-slate-blue-background) 0%,
			var(--gradient-light-royal-blue-background) 100%
		);
		}
	}
</style>
