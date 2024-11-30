<script>
    import { createEventDispatcher } from "svelte";

    let dispatch  = createEventDispatcher();

    let name;
    let beltColour;
    let age
    let skills = [];

    const handleSubmit = () => {
        const person = {
            name,
            beltColour,
            skills,
            id: Math.random()
        }
        dispatch('addPerson', person);
    }
</script>

<form on:submit|preventDefault={handleSubmit}>
    <input type="text" name="" id="" placeholder="name" bind:value={name}>
    <input type="number" placeholder="age" bind:value={age}>
    <br>
    <label>Skills:</label>
    <br>
    <input type="checkbox" name="" id="" bind:group={skills} value="fighting">fighting<br>
    <input type="checkbox" name="" id="" bind:group={skills} value="sneaking">sneaking<br>
    <input type="checkbox" name="" id="" bind:group={skills} value="running">running<br>
    <label >Belt colour</label>
    <br>
    <select bind:value={beltColour}>
        <option value="black">Black</option>
        <option value="orange">Orange</option>
        <option value="brown">Brown</option>
        <option value="yellow">Yellow</option>
        <option value="white">White</option>

    </select>
    <br>
    <button>Add person</button>
</form>

<style>

</style>