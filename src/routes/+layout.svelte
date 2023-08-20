<svelte:head>
	<link
		rel="stylesheet"
		href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@48,400,0,0"
	/>
</svelte:head>

<slot />

<style>
	@import url('https://fonts.googleapis.com/css2?family=Cairo&display=swap');

	:global(*) {
		margin: 0;
		padding: 0;
		border: 0;
		vertical-align: baseline;
		font: inherit;
		font-size: 100%;
		box-sizing: border-box;
		font-family: inherit;
	}

	:global(html) {
		overflow-x: hidden;
		font-family: 'Cairo', sans-serif;
	}
</style>
