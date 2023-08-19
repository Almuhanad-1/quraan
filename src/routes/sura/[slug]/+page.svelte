<script>
	import { onMount } from 'svelte';
	import Header from '../../../components/header.svelte';
	import Modal from '../../../components/modal/modal.svelte';

	export let data;

	let showModal = false;

	let id = data.id; // Your dynamic id
	let sura; // To hold the imported data

	let modal = false;
	let modalTitle = 'title';
	onMount(async () => {
		try {
			// Use the import() function to dynamically load the module
			const dynamicModule = await import(`../../../lib/surasData/${id}.json`);
			sura = dynamicModule.default; // Assuming your data is the default export
		} catch (error) {
			console.error(error);
		}
	});

	function clickHandler(data) {
		showModal = true;
		modalTitle = data['from-to'].join('-');
	}
</script>

{#if sura}
	<Header title={sura.name} />
	<!-- {#if modal} -->
	<Modal bind:showModal title={modalTitle} />
	<!-- {/if} -->
	<main>
		<h2 class="basmalah">
			{sura.id === 1 ? 'بِسْمِ اللَّهِ الرَّحْمَٰنِ الرَّحِيمِ﴿1﴾' : 'بسم الله الرحمن الرحيم'}
		</h2>
		<div class="sura-ayat">
			{#each sura.parts as part}
				<b id={part.id} on:click={() => clickHandler(part)} style="background-color: {part.color};">
					{part.content}
				</b>
			{/each}
		</div>
	</main>
{:else}
	<p>جاري التحميل ...</p>
{/if}

<style>
	.basmalah {
		background-color: #738494;
		color: #ddd;
		width: 100%;
		text-align: center;
		padding: 10px;
		font-size: 28px;
		font-weight: 300;
		font-family: 'Segoe UI', Roboto, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
	}
	.sura-ayat {
		text-align: justify;
		text-justify: inter-word;
	}
	.sura-ayat b {
		padding: 10px;
		line-height: 3;
		word-spacing: 1px;
		font-size: 14px;
		font-weight: normal;
	}
</style>
