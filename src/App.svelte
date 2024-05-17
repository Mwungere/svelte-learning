<script>
	let firstName = 'Jimi';
	let lastName = 'Smith';
	let beltcolor = 'black';

	const handleClick = () => {
		beltcolor = 'orange';
	}

	const handleInput = (e) => {
		beltcolor = e.target.value;
	}
	$: fullName = `${firstName} ${lastName}`
	$: {
		console.log(fullName);
		console.log(beltcolor)
		};
</script>

<main>

	<p>{fullName} - {beltcolor} belt</p>
	<input type="text" bind:value={firstName}>
	<input type="text" bind:value={lastName}>
	<input type="text" bind:value={beltcolor}>
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