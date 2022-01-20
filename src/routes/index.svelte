<script>
	import Site from '$lib/landingPage/Site.svelte';
	import LandingPageHeader from '$lib/landingPage/LandingPageHeader.svelte';
	import Logo from '$lib/landingPage/Logo.svelte';
	import Hero from '$lib/landingPage/sections/hero/Hero.svelte';
	import Benefits from '$lib/landingPage/sections/Benefits.svelte';
	import Section from '$lib/landingPage/sections/Section.svelte';
	import LandingPageForm from '$lib/landingPage/sections/Section.svelte';
	import LandingPageFooter from '$lib/landingPage/sections/LandingPageFooter.svelte';
import Text from '$lib/grabbox/Text.svelte';

	let layout = 'copy'
</script>

<div>
	<button on:click={() => (layout = 'pic-copy')}>Pic Copy</button>
	|
	<button on:click={() => (layout = 'copy-pic')}>Copy Pic</button>
	|
	<button on:click={() => (layout = 'pic')}>Pic</button>
	|
	<button on:click={() => (layout = 'copy')}>Copy</button>
</div>

<Site>
	<LandingPageHeader>
		
	</LandingPageHeader>

	<Hero layout={layout} textColor='#fff'>
		<svelte:fragment slot="overtitle">Slot name : overtitle</svelte:fragment>
		<svelte:fragment slot="title">Slot name : title</svelte:fragment>
		<svelte:fragment slot="explainer">Slot name : explainer</svelte:fragment>
		<svelte:fragment slot="cta">Slot name : cta</svelte:fragment>
		<svelte:fragment slot="details">Slot name : details</svelte:fragment>
	</Hero>

	<!-- <Benefits />

	<Section />

	<LandingPageForm />

	<LandingPageFooter /> -->
</Site>
