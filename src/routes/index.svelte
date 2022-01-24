<script>
	import Site from '$lib/landingPage/Site.svelte';
	import LandingPageHeader from '$lib/landingPage/navigation/LandingPageHeader.svelte';
	import Logo from '$lib/landingPage/Logo.svelte';
	import Hero from '$lib/landingPage/sections/hero/Hero.svelte';
	import Benefits from '$lib/landingPage/sections/Benefits.svelte';
	import Section from '$lib/landingPage/sections/Section.svelte';
	import LandingPageForm from '$lib/landingPage/sections/Section.svelte';
	import LandingPageFooter from '$lib/landingPage/navigation/LandingPageFooter.svelte';
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
			<a href="#_">
				<span class="text-xl font-black leading-none select-none">awesome!</span>
			</a>
		</svelte:fragment>
		<svelte:fragment slot="center">
			<a href="#" class="hover:text-blue-800">Home</a>
			<a href="#" class="hover:text-blue-800">Features</a>
			<a href="#" class="hover:text-blue-800">Blog</a>
			<a href="#" class="hover:text-blue-800">Contact</a>
		</svelte:fragment>
		<svelte:fragment slot="rhs">
			<a href="#_" class="hover:text-blue-800">Sign In</a>
			<a
				href="#_"
				class="inline-items-center justify-center px-4 py-2 mr-1 text-base leading-6 twhitespace-no-wrap duration-150 ease-in-out bg-white border border-transparent rounded-full hover:bg-blue-800 hover:text-white focus:outline-none focus:border-indigo-700 focus:shadow-outline-indigo active:bg-indigo-700"
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

	<MockSection paragraphs={12} />

	<Hero {layout} textColor="#fff">
		<svelte:fragment slot="overtitle">Slot name : overtitle</svelte:fragment>
		<svelte:fragment slot="title">Slot name : title</svelte:fragment>
		<svelte:fragment slot="explainer">Slot name : explainer</svelte:fragment>
		<svelte:fragment slot="cta">Slot name : cta</svelte:fragment>
		<svelte:fragment slot="details">Slot name : details</svelte:fragment>
	</Hero>

	<!-- <Benefits /> -->

	<!-- <Section /> -->

	<!-- <LandingPageForm /> -->

	<LandingPageFooter companyName="awesome." additionalClasses="text-sm font-medium text-gray-500 transition">
		<svelte:fragment slot="lhs">
			<a href="#_" class="text-xl font-black leading-none text-black">awesome!</a>
			<p class="my-4 leading-normal text-gray-500">Some incredibly deep saying.</p>
		</svelte:fragment>

	</LandingPageFooter>
</Site>
