<script>
	import OverallScore from '../lib/components/OverallScore.svelte';
	import Summary from '../lib/components/Summary.svelte';
</script>

<div class="lg:flex rounded-3xl h-full lg:h-auto w-full">
	<OverallScore />
	<Summary />
</div>

<style lang="scss">
    div {
        box-shadow: 0 20px 30px 10px var(--neutral-pale-blue);
    }
</style>
