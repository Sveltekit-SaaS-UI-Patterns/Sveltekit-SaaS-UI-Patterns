<script lang="ts">
	import GoRight from '$lib/icons/GoRight.svelte';
	export let textColor = undefined;
	export let alignment;
	export let parentSlots;

	const copyClasses = `copyConatiner flex flex-col items-${alignment} justify-center w-full lg:max-w-lg`;
	const overtitleClasses =
		'inline-block px-2 py-1 mb-5 font-medium tracking-wider text-gray-900 uppercase bg-gray-200 rounded-full text-xxs';
	const titleClasses = `mb-3 text-3xl font-extrabold leading-none sm:text-4xl lg:text-7xl ${
		alignment === 'center' ? 'text-center' : ''
	}`;
	const explainerClasses = 'py-5 mb-5 lg:text-xl';
	const actionsClasses = 'flex items-center';
	const ctaButtonClasses =
		'inline-flex items-center justify-center h-12 px-6 mr-6 font-medium tracking-wide text-white transition duration-200 bg-gray-900 rounded-lg hover:bg-gray-900 focus:shadow-outline focus:outline-none';
	const detailsLinkClasses =
		'inline-flex items-center text-lg underline transition-colors duration-200';
</script>

<div class={copyClasses} style={`color: ${textColor}`}>
	{#if parentSlots.overtitle}
		<p class={overtitleClasses}><slot name="overtitle" /></p>
	{/if}
	{#if parentSlots.title}
		<h5 class={titleClasses}><slot name="title" /></h5>
	{/if}
	{#if parentSlots.explainer}
		<p class={explainerClasses}><slot name="explainer" /></p>
	{/if}
	{#if parentSlots.cta || parentSlots.details}
		<div class={actionsClasses}>
			{#if parentSlots.cta}
				<button type="submit" class={ctaButtonClasses}>
					<slot name="cta" />
				</button>
			{/if}
			{#if parentSlots.details}
				<a href="/" aria-label="" class={detailsLinkClasses}><slot name="details" /><GoRight /></a>
			{/if}
		</div>
	{/if}
</div>

<style>
</style>
