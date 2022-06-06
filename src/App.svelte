<script lang=ts>

let weight = 135;
let steps = 30000;
    let items = [
        { text: 'chips', amt: 283, cal: 5 },
        { text: 'crunch bar', amt: 4, cal: 160 },
        { text: 'donuts', amt: 2, cal: 300 }
	];

	function add() {
		items = items.concat({ text: '', amt: 1, cal: 4 });
	}

	const remove = (item: { text: string; amt: number; cal: number; }) => {
        items = items.filter(i => i !== item)
	};


	// $: remaining = todos.filter(t => !t.done).length;

	// $: amtSum = list.reduce((acc, list) => acc + list.amt,0)
	// $: calSum = list.reduce((acc, list) => acc + list.cal,0)
	$: foodtotal = items.reduce((acc, list) => acc + list.cal*list.amt,0)
	//$: tool = foodtotal - weight * 

</script>

<h1>Food Diary</h1>

{#each items as item}
	<div>
		<input placeholder="enter item" bind:value={item.text}>
		<input bind:value={item.amt}>
		<input bind:value={item.cal}>
		<button on:click={() => remove(item)}>&times;</button>
	</div>
{/each}

weight
<input bind:value={weight}>
<br>
steps
<input bind:value={steps}>

<!-- <p>{amtSum}</p>
<p>{calSum}</p> -->
<p>{foodtotal}</p>

<button on:click={add}>
	Add item
</button>
