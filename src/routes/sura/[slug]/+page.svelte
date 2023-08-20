<script>
	import { onMount } from 'svelte';
	import Header from '../../../components/header/header.svelte';
	import Modal from '../../../components/modal/modal.svelte';
	import './sura.css';
	export let data;

	let showModal = false;

	let id = data.id; // Your dynamic id
	let sura; // To hold the imported data

	let modalTitle = 'title';
	let location;
	onMount(async () => {
		try {
			// Use the import() function to dynamically load the module
			const dynamicModule = await import(`../../../lib/surasData/${id}.json`);
			sura = dynamicModule.default; // Assuming your data is the default export
		} catch (error) {
			console.error(error);
		}
	});

	function openModal(data) {
		console.log(showModal);
		showModal = true;
		modalTitle = data['from-to'].join('-');
		location = data.location;
	}

	function closeModal() {
		showModal = false;
	}
</script>

{#if sura}
	<Header title={sura.name} />
	{#if showModal}
		<Modal title={modalTitle} {location} {closeModal} />
	{/if}
	<main>
		<h2 class="basmalah">
			{sura.id === 1 ? 'بِسْمِ اللَّهِ الرَّحْمَٰنِ الرَّحِيمِ﴿1﴾' : 'بسم الله الرحمن الرحيم'}
		</h2>
		<div class="sura-ayat">
			{#each sura.parts as part}
				<!-- svelte-ignore a11y-no-static-element-interactions -->
				<!-- svelte-ignore a11y-click-events-have-key-events -->
				<b id={part.id} on:click={() => openModal(part)} style="background-color: {part.color};">
					{part.content}
				</b>
			{/each}
		</div>
	</main>
{:else}
	<p>جاري التحميل ...</p>
{/if}

<style>
</style>
