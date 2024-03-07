<script>
	export let name = 'Jimmy';
	let lastName = 'Hendrix';
	let count = 0;
	let color = 'Red';

	$: fullName =`${name}  ${lastName}` //Reactive value
	$: {
		console.log(color) //Reactive statement
		console.log(fullName)
	}
	const addHandler = ()=>{
		count++;
	}
	
	const userColor = (event)=>{
		color = event.target.value
	}
</script>

<main>
	<p> {fullName} {color} belt</p>
	<input type="text" bind:value={name}>
	<input type="text" bind:value={lastName}>
	<input type="text" bind:value={color}>

<!-- <h1 style="color:{color}">Hello {name}! im {count} years old and i like {color}</h1> 
	<input type="text" on:input={userColor} placeholder="color"> 
		<button	on:click={addHandler}>Click me </button>
		-->
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	p {
		color: #000;
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