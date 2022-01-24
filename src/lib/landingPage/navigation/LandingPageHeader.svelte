<script lang="ts">
	import Close from '$lib/icons/Close.svelte';
	import Hamburger from '$lib/icons/Hamburger.svelte';
	import Benefits from '../sections/Benefits.svelte';

	export let bgColor = 'white';
	export let color = 'black';

    export let additionalClasses = '';

	export let gap = '1rem';
	export let height = '6rem';
	export let position = 'fixed';

	function getPositionClass() {
		if (position === 'fixed') {
			return 'fixed';
		} else if (position === 'float') {
			return 'absolute';
		} else if (position === 'shyfixed') {
			return 'absolute';
		}
	}

	let mobileMenuCollapsed = true;

	const wrapperClasses = `header w-full px-3 antialiased lg:px-6 ${getPositionClass()} ${additionalClasses}`;
	const contentClasses = 'mx-auto max-w-7xl h-full';
	const navClasses =
		'navlist grid h-full content-center w-full select-none items-center justify-center overflow-hidden';

	const mobileExpandClasses =
		'right-0 z-50 flex flex-col items-end w-10 h-10 p-2 mr-4 rounded-full cursor-pointer md:hidden hover:bg-gray-900 hover:bg-opacity-10';

	function toggleMenu() {
		console.log('Toggle : ', mobileMenuCollapsed);
		mobileMenuCollapsed = !mobileMenuCollapsed;
	}

	let y = 0;
	let oldY = 0;
	let oldDirection = 0;
	let offset = 0;
	let headerElement;
	$: {
		const direction = oldY - y > 0 ? 1 : -1;
		if (direction > 0 && oldDirection < 0) {
			headerElement.animate(
				[
					// keyframes
					{ transform: 'translateY(-200px)' },
					{ transform: 'translateY(0px)' }
				],
				{
					duration: 400,
					iterations: 1
				}
			);
		}
		if (direction > 0) {
			offset = y;
		}
		oldDirection = direction;
		oldY = y;
	}
</script>

<svelte:window bind:scrollY={y} />
<section
	bind:this={headerElement}
	class={wrapperClasses}
	style={`background-color: ${bgColor}; color: ${color}; height: ${height}; top: ${offset}px`}
>
	<div class={contentClasses}>
		<nav class={navClasses} style={`gap: ${gap}`}>
			<div class="lhs">
				<slot name="lhs" />
			</div>
			<div
				class="center flex items-center justify-center text-center w-0 md:w-auto invisible md:visible"
				style={`gap: ${gap}`}
			>
				<slot name="center" />
			</div>
			<div class="rhs flex items-center justify-center">
				<div
					class="flex items-center justify-center w-0 md:w-auto invisible md:visible whitespace-nowrap"
					style={`gap: ${gap}`}
				>
					<slot name="rhs" />
				</div>
				<div on:click={toggleMenu} class={mobileExpandClasses}>
					<Hamburger />
				</div>
			</div>
		</nav>
	</div>
	{#if !mobileMenuCollapsed}
		<div class="mobileMenu" style={`gap: ${gap}`}>
			<div on:click={toggleMenu}>
				<Close />
			</div>
			<slot name="lhs" />
			<slot name="center" />
			<slot name="rhs" />
		</div>
	{/if}
</section>

<style>

	.navlist {
		grid-template-columns: min-content 1fr min-content;
	}

	.mobileMenu {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-color: plum;
		z-index: 100;
		display: flex;
		justify-content: center;
		align-items: center;
		flex-direction: column;
		text-align: center;
	}

</style>
