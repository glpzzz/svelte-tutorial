<script>
    let name;
    let beltColor;
    let age;
    let skills = [];

    const handleSubmit = () => {
        console.log(name, beltColor, age, skills);
    }

</script>

<form on:submit|preventDefault={handleSubmit}>
    <div>
        <label for="person-name">Name</label>
        <input id="person-name" type="text" placeholder="name" bind:value={name}/>
    </div>

    <div>
        <label for="person-beltcolor"> Belt Color</label>
        <select id="person-beltcolor" bind:value={beltColor}>
            <option value="white">White</option>
            <option value="blue">Blue</option>
            <option value="red">Red</option>
            <option value="green">Green</option>
            <option value="brown">Brown</option>
            <option value="black">Black</option>
        </select>
    </div>

    <div>
        <label for="person-age">Age</label>
        <input id="person-age" type="number" placeholder="age" bind:value={age}/>
    </div>

    <fieldset>
        <legend>Skills</legend>
        <label>
            <input type="checkbox" value="f" bind:group={skills}/> Fighting
        </label>
        <label>
            <input type="checkbox" value="s" bind:group={skills}/> Sneaking
        </label>
        <label>
            <input type="checkbox" value="r" bind:group={skills}/> Running
        </label>
    </fieldset>

    <input type="submit" value="Add Person"/>
</form>

<style></style>
