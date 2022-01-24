<script lang="ts">
	import Copy from './Copy.svelte';

	/** Background color of section. Defaults to transparent */
	export let bgColor = 'transparent';

	/** Background image. Defaults to to tacos */
	export let imgUrl = 'https://www.pexels.com/photo/4577740/download';

	/** Text color of copy. Defaults to to inherit */
	export let textColor = 'inherit';

	/** Layout of hero. Can be ['pic-copy', 'copy-pic', 'pic', 'copy'] */
	export let layout;

	/**
	 * Alignment of text. Can be start, end, or center.
	 * For two column layouts, defaults to start.
	 * For one column layout defaults to center
	 **/
	export let alignment = undefined;

	const computeAlignment = (value) => (['pic', 'copy'].includes(value) ? 'center' : 'start');

	let copyAttrs;
	$: copyAttrs = {
		textColor,
		parentSlots: $$slots,
		alignment: alignment ? alignment : computeAlignment(layout)

	};

	const sectionClasses = 'section flex flex-col w-full overflow-hidden lg:flex-row sm:mx-auto';
	const copyContainer = 'lhs flex justify-end p-8 lg:py-32 lg:px-16 lg:pl-10 lg:w-1/2';
	const pictureContainer = 'rhs relative lg:w-1/2';

</script>

<section class={sectionClasses} style={`background-color: ${bgColor}`}>
	{#if layout === 'pic-copy'}
		<div class={pictureContainer}>
			<img src={imgUrl} class="object-cover w-full lg:absolute h-80 lg:h-full" />
		</div>
		<div class={copyContainer}>
			<Copy {...copyAttrs}>
				<slot name="overtitle" slot="overtitle" />
				<slot name="title" slot="title" />
				<slot name="explainer" slot="explainer" />
				<slot name="cta" slot="cta" />
				<slot name="details" slot="details" />
			</Copy>
		</div>
	{:else if layout === 'copy-pic'}
		<div class={copyContainer}>
			<Copy {...copyAttrs}>
				<slot name="overtitle" slot="overtitle" />
				<slot name="title" slot="title" />
				<slot name="explainer" slot="explainer" />
				<slot name="cta" slot="cta" />
				<slot name="details" slot="details" />
			</Copy>
		</div>
		<div class={pictureContainer}>
			<img src={imgUrl} class="object-cover w-full lg:absolute h-80 lg:h-full" />
		</div>
	{:else if layout === 'pic'}
		<div
			class="heroContainer grid place-items-center w-full bg-fixed bg-cover bg-center"
			style={`background-image: url('${imgUrl}')`}
		>
			<Copy {...copyAttrs}>
				<slot name="overtitle" slot="overtitle" />
				<slot name="title" slot="title" />
				<slot name="explainer" slot="explainer" />
				<slot name="cta" slot="cta" />
				<slot name="details" slot="details" />
			</Copy>
		</div>
	{:else if layout === 'copy'}
		<div class="heroContainer grid place-items-center w-full">
			<Copy {...copyAttrs}>
				<slot name="overtitle" slot="overtitle" />
				<slot name="title" slot="title" />
				<slot name="explainer" slot="explainer" />
				<slot name="cta" slot="cta" />
				<slot name="details" slot="details" />
			</Copy>
		</div>
	{:else}
		<div class="heroContainer grid place-items-center w-full">
			<h1>
				Missing Layout. Defaulting to just <code>copy</code>. Can be one of
				<code>['pic-copy', 'copy-pic', 'pic', 'copy']</code>
			</h1>
			<Copy {...copyAttrs}>
				<slot name="overtitle" slot="overtitle" />
				<slot name="title" slot="title" />
				<slot name="explainer" slot="explainer" />
				<slot name="cta" slot="cta" />
				<slot name="details" slot="details" />
			</Copy>
		</div>
	{/if}
</section>

<style>
	.section {
		min-height: 80vh;
	}

	.heroContainer {
		min-height: 80vh;
	}
</style>
