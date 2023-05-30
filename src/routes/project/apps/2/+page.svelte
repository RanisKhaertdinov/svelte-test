<script>

	let itemName = '';
	let itemAmount = '';
	let expenditure = [];
	// amount = +amount;

	function checker () {
		if (itemName !== '' && itemAmount !== '') {
			addExpense();
		} 
	}

	function addExpense() {
		const object = {
			Title: itemName,
			Amount: itemAmount
		};
		expenditure.push(object);
		expenditure = expenditure;
		itemName = '';
		itemAmount = '';
	}
	
	function deleteExpense(index) {
		expenditure.splice(index, 1);
		expenditure = expenditure;
	}

</script>


	<h1>Учет расходов</h1>

	<p>Название:</p>
	<input bind:value={itemName}>
	<p>Сумма:</p>
	<input bind:value={itemAmount}>
	<button class="add-expenditure" on:click= {checker}>Добавить</button>

		<table>
			<thead>
				<tr>
					<th>Название</th>
					<th class="center-column">Сумма</th>
					<th>Действие</th>
				</tr>
			</thead>
			<tbody>
				{#each expenditure as item, index}
					<tr>
						<td><div>{item.Title}</div></td>
						<td class="center-column"><div>{item.Amount}</div></td>
						<td>
							<button on:click={() => deleteExpense(index)}>Удалить</button>
						</td>
					</tr>
				{/each}
			</tbody>
		</table>



<style>
	table {
		margin: 20px 0;
		min-width: 800px;
		min-height: 100%;
		align-content: center;
		border: 1px solid lightgray;
		box-shadow:  0 0 15px rgb(0, 0, 0 / 20%);
	}
	th {
		border: 1px solid lightgray;
		border-top: none;
	}
	.center-column {
		border-right: none;
		border-left: none;
	}
	td {
		text-align: center;
		border: 1px solid lightgray;
		border-top: none;
	}
</style>