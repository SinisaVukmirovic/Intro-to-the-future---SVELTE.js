<script>
    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher()

	export let name;
	export let points;
	let showControls = false;

	const addPoint = () => points += 1;
	const removePoint = () => points -= 1;

    const toggleControls = () => showControls = !showControls;
    
    const onDelete = () => dispatch('removeplayer', name);
</script>

<style>
	h1 {
        color: var(--primary-color);
	}

	h3 {
        margin: 1rem 2rem;
        font-size: 2rem;
	}
</style>

<div class="card">
    <h1>
        {name}
        <button class="btn btn-success" on:click={toggleControls}>
            {#if showControls}Hide Controls{:else}Show Controls{/if}
        </button>
        <button class="btn btn-danger" on:click={onDelete}>Delete Player</button>
    </h1>
    <h3>{points}</h3>
    
    {#if showControls}
        <span>Add/Remove Points: </span>
        <button class="btn" on:click={addPoint}>+1</button>
        <button class="btn btn-dark" on:click={removePoint}>-1</button>

        <input type="number" bind:value={points}>
    {/if}
</div>

