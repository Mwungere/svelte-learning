<script>

    let name;
    let beltcolor;
    let age;
    let skills = [];

    const handleSubmit = () => {

        console.log(name, beltcolor, age, skills);
    }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input type="text" name="name" placeholder="name" bind:value={name}/>		
    <input type="number" placeholder="age" bind:value={age}/>
    <label>Skills:</label>
    <input type="checkbox" bind:group={skills} value="fighting">fighting <br>
    <input type="checkbox" bind:group={skills} value="sneaking">sneaking <br>
    <input type="checkbox" bind:group={skills} value="running">running <br>	
    <label>Belt color: </label>
    <select bind:value={beltcolor}>
        <option value="green">Green</option>
        <option value="orange">Orange</option>
        <option value="brown">Brown</option>
        <option value="white">White</option>

    </select>
    <button>Add Person</button>	

</form>


<style>

</style>