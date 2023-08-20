<script>
	import { onMount } from 'svelte';

	export let title;
	export let closeModal;
	export let location;

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
		alert(`"${note}" \n your note is saved`);
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
								<p>التّفْصيْلُ الموضوعِي {title}:<br />'هنا ينبغي ان يظهر التفصيل'</p>
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
	.modal-backdrop,
	.modal-backdrop-bg {
		position: fixed;
		top: 0;
		left: 0;
		z-index: 5;
		width: 100%;
		height: 100%;
	}

	.modal-backdrop-bg {
		transition: opacity 300ms ease-in-out;
		background-color: #000;
		pointer-events: none;
	}

	.modal-backdrop-bg {
		opacity: 0.5;
	}

	.modal {
		width: 50%;
		margin: auto;
		background-color: #414042;
		border-radius: 10px;
		box-shadow: 5px 5px 8px #414042;
		height: 50%;
		z-index: 10;
		position: absolute;
		top: 0;
		right: 0;
		bottom: 0;
		left: 0;
		overflow: hidden;
	}

	.modal-header {
		background: #404040;
		color: #ddd;
		padding: 5px;
		display: flex;
		justify-content: right;
		position: relative;
		height: 50px;
	}

	.modal-header .title {
		display: block;
		position: absolute;
		top: 0;
		left: 50%;
		transform: translateX(-50%);
		font-size: 17px;
		line-height: 44px;
	}

	.modal-header button {
		font-weight: bolder;
		margin-right: 2%;
		border-color: transparent;
		background: none;
		box-shadow: none;
		color: #ddd;
		font-size: 17px;
		padding-right: 2px;
		padding-left: 2px;
		line-height: 32px;
	}
	.modal-content .card .item .list span#_label-0 {
		font-size: 32px;
		color: #414042;
		display: block;
		text-align: center;
		max-width: 100%;
		width: 100%;
	}

	.modal-content .card .item .list span#_label-0:before {
		content: '';
		display: inline-block;
		border: 1px solid #414042;
		width: 15px;
		background: #414042;
		height: 15px;
		margin-left: 2%;
		border-radius: 0 10px 10px 0;
	}

	.modal-content .card .item .list span#_label-0:after {
		content: '';
		display: inline-block;
		border: 1px solid #414042;
		width: 15px;
		background: #414042;
		height: 15px;
		margin-right: 2%;
		border-radius: 10px 0 0 10px;
	}

	.modal-content .card .item .list .ng-pristine {
		display: block;
		width: 100%;
		border: 2px solid #414042;
		padding: 3% 2%;
		margin-bottom: 5%;
		margin-top: 5%;
	}

	.modal-content .card .item .list .button {
		background: #414042;
		padding: 1%;
		color: #fcfcfc;
		max-width: 35%;
		margin: auto;
		font-size: 24px;
		border-radius: 10px;
	}

	.modal-content .card .item .list .button:hover {
		background: none;
		color: #414042;
		box-shadow: 5px 5px 8px #414042;
	}

	.modal-content h1 {
		display: none;
	}
	.modal-content .card .item .list span#_label-0 {
		font-size: 32px;
		color: #414042;
		display: block;
		text-align: center;
		max-width: 100%;
		width: 100%;
	}

	.modal-content .card .item .list span#_label-0:before {
		content: '';
		display: inline-block;
		border: 1px solid #414042;
		width: 15px;
		background: #414042;
		height: 15px;
		margin-left: 2%;
		border-radius: 0 10px 10px 0;
	}

	.modal-content .card .item .list span#_label-0:after {
		content: '';
		display: inline-block;
		border: 1px solid #414042;
		width: 15px;
		background: #414042;
		height: 15px;
		margin-right: 2%;
		border-radius: 10px 0 0 10px;
	}

	.modal-content .card .item .list .ng-pristine {
		display: block;
		width: 100%;
		border: 2px solid #414042;
		padding: 3% 2%;
		margin-bottom: 5%;
		margin-top: 5%;
	}

	.modal-content .card .item .list .button {
		background: #414042;
		padding: 1%;
		color: #fcfcfc;
		max-width: 35%;
		width: 100%;
		margin: auto;
		font-size: 24px;
		border-radius: 10px;
	}

	.modal-content .card .item .list .button:hover {
		background: none;
		color: #414042;
		box-shadow: 5px 5px 8px #414042;
	}

	.modal-content h1 {
		display: none;
	}

	.card,
	.list-inset {
		overflow: hidden;
		margin: 20px 10px;
		border-radius: 2px;
		background-color: #fff;
	}

	.card {
		padding-top: 1px;
		padding-bottom: 1px;
		box-shadow: 0 1px 3px rgba(0, 0, 0, 0.3);
	}
	.card .item {
		border-left: 0;
		border-right: 0;
	}
	.card .item:first-child {
		border-top: 0;
	}
	.card .item:last-child {
		border-bottom: 0;
	}

	.list h2 {
		background: #000;
		color: #fff;
		padding: 10px;
	}

	.list label {
		display: block;
	}

	.list button {
		display: block;
		font-family: '-apple-system', 'Helvetica Neue', 'Roboto', 'Segoe UI', sans-serif;
	}

	.list input,
	.list input:focus-visible {
		border: 0;
		outline: 0;
		font-size: 16px;
		font-weight: normal;
		font-family: '-apple-system', 'Helvetica Neue', 'Roboto', 'Segoe UI', sans-serif;
		line-height: 1.2;
	}
	.card .item {
		padding: 16px;
	}

	.item p {
		color: #666;
		font-size: 14px;
		margin-bottom: 2px;
	}

	.item h2 {
		margin: 0 0 2px 0;
		font-size: 16px;
		font-weight: normal;
		font-family: '-apple-system', 'Helvetica Neue', 'Roboto', 'Segoe UI', sans-serif;
		line-height: 1.2;
	}

	.input-label {
		display: table;
		padding: 7px 10px 7px 0px;
		max-width: 200px;
		width: 35%;
		color: #444;
		font-size: 16px;
	}
</style>
