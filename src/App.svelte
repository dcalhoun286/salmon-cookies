<script>
	import { storeData } from "./store.js";
		function updateStore(e){
			
		}
		import Table from './Table.svelte';
	</script>
	
	<style>
		.content {
			display: grid;
			grid-template-columns: 20% 80%;
			grid-column-gap: 10px;
		}
	</style>
	
	<h1>New Location</h1>
	<form class="content" on:submit|preventDefault={updateStore}>
		<label>City</label>
		<input type="text" bind:value={$storeData.name} />
		<label>Max Customers Per Hour</label>
		<input type="text" bind:value={$storeData.email} />
		<label>Min Customers Per Hour</label>
		<input type="text" bind:value={$storeData.phone} />
		<label>Average Cookie Sales Per Hour</label>
		<input type="text" bind:value={$storeData.avgCookie} />
		<input type="submit" value="submit" />
	</form>
	
		<p>
		{JSON.stringify($storeData, 0, 2)}
	</p>
	<Table />