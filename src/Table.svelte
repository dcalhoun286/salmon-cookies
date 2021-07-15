<script>
	import Tables from './Tables.svelte';
	const hoursArray = ['','6', '7', '8', '9', '10', '11', '12', '13', '14', '15', '16', '17', '18', '19'];
	export const locationsArray = [];
JSON.stringify(locationsArray, 0, 2);
	// const cookies = {}
	export const hourlyTotalsArray = [0,0,0,0,0,0,0,0,0,0,0,0,0,0];
	let dailyTotalAllLocations = 0;
	
	class NewLocation {
		constructor(city, minCustomers, maxCustomers, avgCookies) {
	this.city = city,
	this.minCustomers = minCustomers,
	this.maxCustomers = maxCustomers,
	this.avgCookies = avgCookies,
	this.simSalesDayArray = [];
	this.dailyTotal = 0;
		}
		
	rndmCustomers(minCustomers, maxCustomers) {
		minCustomers = Math.ceil(minCustomers);
		maxCustomers = Math.floor(maxCustomers);
		return Math.floor(Math.random() * (maxCustomers- minCustomers + 1) + minCustomers);
	}
		
		simulatedSalesDay() {
			let salesForHour;
			for (let i = 0; i < hoursArray.length-1; i++) {
				let listr = '';
				salesForHour = Math.ceil(this.rndmCustomers(this.minCustomers, this.maxCustomers) * this.avgCookies);

    this.dailyTotal += salesForHour;
		
    listr = salesForHour;

    var oldSalesForHour;
    oldSalesForHour = hourlyTotalsArray[i];
    salesForHour = salesForHour + oldSalesForHour;
    hourlyTotalsArray[i] = salesForHour;
				console.log(hourlyTotalsArray[i]);
				console.log('salesForHour', salesForHour);
				console.log('oldSales', oldSalesForHour);
				console.log('listr', listr);
    this.simSalesDayArray.push(listr);
				
			}
			dailyTotalAllLocations += this.dailyTotal;
  locationsArray.push(this);
		}
		
	}
	
	let seattle = new NewLocation('Seattle', 65, 23, 6.3);
	seattle.simulatedSalesDay();
	let austin = new NewLocation('Austin', 44, 33, 2.8);
	austin.simulatedSalesDay();
	export let tableData = locationsArray;
</script>
<style>
</style>

<body>
  <!-- <table>
    <thead>
      <tr>
        {#each hoursArray as item}
		<th>{item}</th>
	{/each}
      </tr>
    </thead>
    <tbody>
			{#each locationsArray as item}
		<tr>{item.city}</tr>
		
	{/each}
    </tbody>
  </table> -->
	<Tables tableData={locationsArray} hourlyTotalsArray={hourlyTotalsArray} totalOfTotals={dailyTotalAllLocations}/>

</body>
