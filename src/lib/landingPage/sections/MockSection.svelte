<script lang="ts">
	export let paragraphs = 4;
	let wordsPerzParagraph = 100;
	let maxWordLength = 13;

	// generates text with repeating . of length 1 to maxWordLength
	function generateText(maxWordLength) {
		let text = '';
		for (let i = 0; i < maxWordLength; i++) {
			text += 'A';
		}
		return text;
	}

	// generates an array of 50 to wordsPerzParagraph word
	function generateWords(wordsPerzParagraph) {
		let words = [];
		for (let i = 0; i < wordsPerzParagraph; i++) {
			words.push(generateText(Math.floor(Math.random() * maxWordLength)));
		}
		return words;
	}

	// create an array of paragraphs
	function generateParagraphs(paragraphs) {
		let paragraphsArray = [];
		for (let i = 0; i < paragraphs; i++) {
			paragraphsArray.push(generateWords(wordsPerzParagraph));
		}
		return paragraphsArray;
	}

	const copy: string[][] = generateParagraphs(paragraphs);
</script>

<section class="w-full px-3 antialiased lg:px-6 s-4RtoogHfbJSi">
	<div class="mx-auto max-w-7xl h-full s-4RtoogHfbJSi">
		<h1>
			<span class="mock">Some</span> <span class="mock">Fake</span> <span class="mock">Title</span>
		</h1>
		{#each copy as p}
			<p>
				{#each p as w}
					<span class="mock">{w}</span> &nbsp;
				{/each}
			</p>
		{/each}
	</div>
</section>

<style>
	h1 {
		margin-top: 2rem;
		font-size: 24px;
	}

	.mock {
		background: #888;
		color: #888;
	}

	p {
		margin-top: 2rem;
		margin-bottom: 2rem;
	}
</style>
