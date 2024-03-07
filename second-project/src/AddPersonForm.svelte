<script>
    import {createEventDispatcher} from 'svelte';

    let dispatch = createEventDispatcher();
     let name;
     let beltColour;
     let age;
    let skills = []

     const handleSubmit = ()=>{
       const person = {
        name:name,
        beltColour: beltColour,
        age:age,
        skills:skills,
        id:Math.random()
       };
       dispatch('addPerson',person)
     }
     
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input type="text" placeholder="name" bind:value={name}>

    <input type="number" placeholder="age" bind:value={age}>

    <label>Skills: </label>
    <input type="checkbox" bind:group={skills} value="fighting">Fighting <br>
    <input type="checkbox" bind:group={skills} value="sneaking">sneaking <br>
    <input type="checkbox" bind:group={skills} value="running">running <br>

    <label>Belt color: </label>
    <select bind:value={beltColour}>

        <option value ="black">Black</option>
        <option value ="brown">Brown</option>
        <option value ="purple">Purple</option>
        <option value ="bue">Blue</option>
        <option value ="white">white</option>

    </select>
    <!-- 
     <input type="checkbox" bind:checked={fighting}>Fighting <br>
    <input type="checkbox" bind:checked={sneaking}>sneaking <br>
    <input type="checkbox" bind:checked={running}>running <br>
    -->
    
   
    
    <button>Add a person</button>
</form>

<style>

</style>