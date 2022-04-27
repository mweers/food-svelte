<script lang=ts>

    let items = [
        { i: 1, text: 'chips', amt: 283, cal: 5 },
        { i: 2, text: 'crunch bar', amt: 4, cal: 160 },
        { i: 3, text: 'donuts', amt: 2, cal: 300 }
	];

	function add() {
		items = items.concat({ i: 4, text: '', amt: 1, cal: 4 });
	}

	const remove = (item: { i: number; text: string; amt: number; cal: number; }) => {
        items = items.filter(i => i !== item)
	};


	// $: remaining = todos.filter(t => !t.done).length;

	// $: amtSum = list.reduce((acc, list) => acc + list.amt,0)
	// $: calSum = list.reduce((acc, list) => acc + list.cal,0)
	$: total = items.reduce((acc, list) => acc + list.cal*list.amt,0)

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

<!-- <p>{amtSum}</p>
<p>{calSum}</p> -->
<p>{total}</p>

<button on:click={add}>
	Add item
</button>
