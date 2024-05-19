<script>
	import Modal from './Modal.svelte'

	let showModal = false;
	const toggleModal = () => {
		showModal = !showModal;
	}
	let people = [
		{name: 'yoshi', beltcolor:'black', age:25, id: 1},
		{name: 'mario', beltcolor: 'orange', age:25, id: 2},
		{name: 'luigi', beltcolor: 'black', age:25, id: 3},
        {name: 'peach', beltcolor: 'green', age:25, id: 4},
        {name: 'bowser', beltcolor: 'blue', age:25, id: 5},
	]

	const handleDelete = (id) => {
		// delete tthe person from people
		people= people.filter((person) => person.id != id)
	}

	
</script>
<Modal message="Hey, I am a prop value" isPromo={true} {showModal} on:click={toggleModal}/>
<main>
	<button on:click={toggleModal}>Open Modal</button>
	{#each people as p (p.id)}
		<div>
			<h4>{p.name}</h4>
			{#if p.beltcolor === 'black'}
				<p><strong>Master Ninja</strong></p>
			{/if}
			<p>{p.age} years old, {p.beltcolor} belt</p>
			<button on:click={() => handleDelete(p.id)}>delete</button>
		</div>
	{:else}
		<p>There are no people to show</p>	
	{/each}
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>