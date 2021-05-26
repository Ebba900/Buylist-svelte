<title> Inköpslista</title>
<script>
    let newItem = '';
	
    let thingsToBuy = [{text: '', status: true},
                    {text: '', status: false},
                    {text: '', status: false}];
	
	function addToList() {
		thingsToBuy = [...thingsToBuy, {text: newItem, status: false}];
		newItem = '';
	}
	
	function removeFromList(index) {
		thingsToBuy.splice(index, 1)
		thingsToBuy = thingsToBuy;
    }
</script>
<main>
<input bind:value={newItem} type="text" placeholder="Nytt inköp..">
<button on:click={addToList}>lägg till</button>
</main>
<br/>
{#each thingsToBuy as item, index}
	<input bind:checked={item.status} type="checkbox">
	<span class:checked={item.status}>{item.text}</span>
	<span on:click={() => removeFromList(index)}>Tabort</span>
	<br/>
{/each} 


<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>