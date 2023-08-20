<script>
	import './header.css';

	export let title;
	export let backBtn = true;
	// export let backBtn_value = 'الفهرس';
</script>

<svelte:head>
	<title>{title}</title>
</svelte:head>

<header>
	<h1 class="sura-name">{title}</h1>
	{#if backBtn}
		<a class="back-btn" href="/playlist">
			<span>الفهرس</span>
			<span class="material-symbols-outlined icon"> arrow_back_ios </span>
		</a>
	{/if}
</header>
