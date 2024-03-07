<script>
	import Modal from "./Modal.svelte";
	import AddPersonForm from "./AddPersonForm.svelte";
	let people = [
		 {name: 'yoshi', beltColour:'Black',age:25,id:1},
		 {name: 'Carlos', beltColour:'white',age:22,id:2},
		 {name: 'Panchp', beltColour:'Blue',age:21,id:3},
	]
	const handleClick = (id)=>{
		//Delete person from people
		people = people.filter((person)=>{
			return person.id != id //It checks if the id that we click is different than the
							//id of the person
		})
		
	}
	//let num = 3;
	let showModal = false;
	const toggleModal = ()=>{
		showModal = !showModal;
	}
	const addPersonForm = (event)=>{
		console.log(event.detail);
		const person = event.detail;
		people = [person, ...people]
	}
</script>
<!--
{#if num > 20}
	<p>Greater than 20</p>
{:else if num > 5}
	<p>Greater than 5</p>
{:else}
	<p>Not greater than 5</p>
{/if}
-->
<Modal {showModal} on:click={toggleModal}> 
	<AddPersonForm  on:addPerson={addPersonForm} />
</Modal>
<main>
	<button on:click|once={toggleModal}>Open modal </button>
	<!--Iterating over the person list-->
	{#each people as person (person.id)}
	<div>
		<h4>{person.name}</h4>
		<!-- Conditional for belt color-->
		{#if person.beltColour.toLowerCase() === 'black'}
			<p> <strong> Master ninja</strong></p>
		{/if}

		<p>{person.age} years old, {person.beltColour} belt</p>
		<button on:click={ ()=>handleClick(person.id) }>Delete</button>
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

	

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
