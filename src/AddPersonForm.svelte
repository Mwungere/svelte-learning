<script>

    let name;
    let beltcolor;
    let age;
    const handleSubmit = () => {

        console.log(name, beltcolor, age);
    }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input type="text" name="name" placeholder="name" bind:value={name}/>		
    <input type="text" name="name" placeholder="belt colour" bind:value={beltcolor}/>
    <input type="number" placeholder="age" bind:value={age}/>	
    <button>Add Person</button>	

</form>


<style>

</style>