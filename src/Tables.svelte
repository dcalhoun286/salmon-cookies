<script>
	export let tableData;
	export let hourlyTotalsArray;
	console.log('hourlytotals', hourlyTotalsArray);
	export const hoursArray = ['', '6', '7', '8', '9', '10', '11', '12', '13', '14', '15', '16', '17', '18', '19', ' Daily Total'];
	export let totalOfTotals;
</script>
<style>
	td {
		padding: 10px;
	}
	th {
		
	}
</style>
<thead>
  <tr>
    {#each hoursArray as columnHeading}
      <th>{columnHeading}</th>
    {/each}
  <tr/>
</thead>
<tbody>
  {#each tableData as city}
    <tr>
			{city.city}
      {#each city.simSalesDayArray as cell}
        <td>{cell}</td>
      {/each}
				<td>{city.dailyTotal}</td>
    </tr>
  {/each}
	</tbody>
	<tfoot>
		<tr>
			hourly totals
			{#each hourlyTotalsArray as columnHeading}
			<th>{columnHeading}</th>
			{/each}
			<th>{totalOfTotals}</th>
		</tr>
	</tfoot>



