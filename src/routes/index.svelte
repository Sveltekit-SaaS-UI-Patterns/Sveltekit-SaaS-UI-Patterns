<script>
	import Site from '$lib/landingPage/Site.svelte';
	import LandingPageHeader from '$lib/landingPage/LandingPageHeader.svelte';
	import Logo from '$lib/landingPage/Logo.svelte';
	import Hero from '$lib/landingPage/sections/hero/Hero.svelte';
	import Benefits from '$lib/landingPage/sections/Benefits.svelte';
	import Section from '$lib/landingPage/sections/Section.svelte';
	import LandingPageForm from '$lib/landingPage/sections/Section.svelte';
	import LandingPageFooter from '$lib/landingPage/sections/LandingPageFooter.svelte';
import MockSection from '$lib/landingPage/sections/MockSection.svelte';

	let layout = 'pic';
</script>

<!-- <div>
	<button on:click={() => (layout = 'pic-copy')}>Pic Copy</button>
	|
	<button on:click={() => (layout = 'copy-pic')}>Copy Pic</button>
	|
	<button on:click={() => (layout = 'pic')}>Pic</button>
	|
	<button on:click={() => (layout = 'copy')}>Copy</button>
</div> -->

<Site>
	<LandingPageHeader position="shyfixed" additionalClasses="shadow-lg">
		<svelte:fragment slot="lhs">
			<a href="#_" >
				<span class="text-xl font-black leading-none select-none">
					<span>awesome.</span>
				</span>
			</a>
		</svelte:fragment>
		<svelte:fragment slot="center">
			<a href="#" class="hover:text-white">Home</a>
			<a href="#" class="hover:text-white">Features</a>
			<a href="#" class="hover:text-white">Blog</a>
			<a href="#" class="hover:text-white">Contact</a>
		</svelte:fragment>
		<svelte:fragment slot="rhs">
			<a href="#_" class="hover:text-white">Sign In</a>
			<a
				href="#_"
				class="inline-flex items-center justify-center px-4 py-2 mr-1 text-base font-medium leading-6 twhitespace-no-wrap transition duration-150 ease-in-out bg-white border border-transparent rounded-full hover:bg-purple focus:outline-none focus:border-indigo-700 focus:shadow-outline-indigo active:bg-indigo-700"
				>Sign Up</a
			>
		</svelte:fragment>
	</LandingPageHeader>

	<Hero {layout} textColor="#fff">
		<svelte:fragment slot="overtitle">Slot name : overtitle</svelte:fragment>
		<svelte:fragment slot="title">Slot name : title</svelte:fragment>
		<svelte:fragment slot="explainer">Slot name : explainer</svelte:fragment>
		<svelte:fragment slot="cta">Slot name : cta</svelte:fragment>
		<svelte:fragment slot="details">Slot name : details</svelte:fragment>
	</Hero>

	<MockSection paragraphs={12}/>
	

	<!-- <Benefits />

	<Section />

	<LandingPageForm />

	<LandingPageFooter /> -->
</Site>
