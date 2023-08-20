<script>
	import { onMount } from 'svelte';
	import './modal.css';

	export let title;
	export let closeModal;
	export let location;
	export let meaning;

	let note = '';
	function bgClickHandler(e) {
		if (e.target === this) {
			closeModal();
		}
	}

	onMount(() => {
		if (!localStorage.getItem(location)) return;
		note = localStorage.getItem(location);
	});

	function saveNoteHandler() {
		localStorage.setItem(location, note);
		// alert(`"${note}" \n your note is saved`);
		closeModal();
	}
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div class="modal-backdrop" on:click={bgClickHandler}>
	<div class="modal-backdrop-bg" />

	<div class="modal-wrapper">
		<div class="modal">
			<header class="modal-header" style="direction: rtl;">
				<button on:click={closeModal}> رجوع </button>
				<h1 class="title">{title}</h1>
			</header>
			<div class="modal-content">
				<div class="card">
					<div class="item item-text-wrap">
						<div class="list">
							<label>
								<p>التّفْصيْلُ الموضوعِي {title}:<br />{meaning}</p>
								<br />
								<h2>ملاحظاتك:<br /> {note}</h2>
								<span class="input-label">إضافة ملاحظة</span>
								<input bind:value={note} type="text" placeholder="اكتـب ملاحـظتك" ng-model="note" />
							</label>
							<button class="button button-full button-positive" on:click={saveNoteHandler}>
								حفظ
							</button>
						</div>
					</div>
				</div>
			</div>
		</div>
	</div>
</div>

<style>
</style>
