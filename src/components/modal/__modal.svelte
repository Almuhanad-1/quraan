<div class="modal-backdrop">
	<div class="modal-backdrop-bg" />

	<div class="modal-wrapper" ng-transclude="">
		<div class="modal">
			<header class="modal-header" style="direction: rtl;">
				<button
					class="button icon-right icon-chevron-left button-clear button-dark"
					style="font-weight:bolder; margin-right: 2%"
					ng-click="closeModal()"
				>
					رجوع
				</button>
				<h1 class="title">{{ group }}</h1>
			</header>
			<ion-content>
				<div class="card">
					<div class="item item-text-wrap">
						<div class="list">
							<label>
								<!-- <p>التّفْصيْلُ الموضوعِي {{group}}:</br>{{mean}}</p></br> -->

								<!-- <h2>ملاحظاتك:</br>{{note}}</h2> -->
								<span class="input-label">إضافة ملاحظة</span>
								<input type="text" placeholder="اكتـب ملاحـظتك" ng-model="note" />
							</label>
							<button class="button button-full button-positive" ng-click="addNesDesc(key,note)">
								حفظ
							</button>
						</div>
					</div>
				</div>
			</ion-content>
		</div>
	</div>
</div>

<style>
	.modal {
		width: 50%;
		margin: auto;
		background-color: #414042;
		border-radius: 10px;
		box-shadow: 5px 5px 8px #414042;
		height: 45%;
		z-index: 10;
	}

	.modal-header {
		background: #404040;
		direction: rtl;
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
	ion-content .card .item .list span#_label-0 {
		font-size: 32px;
		color: #414042;
		display: block;
		text-align: center;
		max-width: 100%;
		width: 100%;
	}

	ion-content .card .item .list span#_label-0:before {
		content: '';
		display: inline-block;
		border: 1px solid #414042;
		width: 15px;
		background: #414042;
		height: 15px;
		margin-left: 2%;
		border-radius: 0 10px 10px 0;
	}

	ion-content .card .item .list span#_label-0:after {
		content: '';
		display: inline-block;
		border: 1px solid #414042;
		width: 15px;
		background: #414042;
		height: 15px;
		margin-right: 2%;
		border-radius: 10px 0 0 10px;
	}

	ion-content .card .item .list .ng-pristine {
		display: block;
		width: 100%;
		border: 2px solid #414042;
		padding: 3% 2%;
		margin-bottom: 5%;
		margin-top: 5%;
	}

	ion-content .card .item .list .button {
		background: #414042;
		padding: 1%;
		color: #fcfcfc;
		max-width: 35%;
		margin: auto;
		font-size: 24px;
		border-radius: 10px;
	}

	ion-content .card .item .list .button:hover {
		background: none;
		color: #414042;
		box-shadow: 5px 5px 8px #414042;
	}

	ion-content h1 {
		display: none;
	}
	ion-content .card .item .list span#_label-0 {
		font-size: 32px;
		color: #414042;
		display: block;
		text-align: center;
		max-width: 100%;
		width: 100%;
	}

	ion-content .card .item .list span#_label-0:before {
		content: '';
		display: inline-block;
		border: 1px solid #414042;
		width: 15px;
		background: #414042;
		height: 15px;
		margin-left: 2%;
		border-radius: 0 10px 10px 0;
	}

	ion-content .card .item .list span#_label-0:after {
		content: '';
		display: inline-block;
		border: 1px solid #414042;
		width: 15px;
		background: #414042;
		height: 15px;
		margin-right: 2%;
		border-radius: 10px 0 0 10px;
	}

	ion-content .card .item .list .ng-pristine {
		display: block;
		width: 100%;
		border: 2px solid #414042;
		padding: 3% 2%;
		margin-bottom: 5%;
		margin-top: 5%;
	}

	ion-content .card .item .list .button {
		background: #414042;
		padding: 1%;
		color: #fcfcfc;
		max-width: 35%;
		margin: auto;
		font-size: 24px;
		border-radius: 10px;
	}

	ion-content .card .item .list .button:hover {
		background: none;
		color: #414042;
		box-shadow: 5px 5px 8px #414042;
	}

	ion-content h1 {
		display: none;
	}
</style>
