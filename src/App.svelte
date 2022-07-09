<script>

    let people = [
        {name: 'Yoshi', beltColor: 'black', age: 25, id: 1},
        {name: 'Mario', beltColor: 'orange', age: 45, id: 2},
        {name: 'Luigi', beltColor: 'brown', age: 35, id: 3},
    ];

    const handleClick = (e, id) => {
        // print the event
        console.log(e);
        // delete the person from people
        people = people.filter(person => person.id !== id);
    }
</script>

<main>
    <h1>People</h1>
    <ul>
        {#each people as person (person.id)}
            <li>
                <h2>{person.name}</h2>
                <p>It's {person.age} and has a {person.beltColor} belt.</p>
                <p>
                    <button on:click={(e) => handleClick(e, person.id)}>Delete</button>
                </p>
            </li>
        {:else}
            <p>There are no people to show</p>
        {/each}
    </ul>

    <hr>

    <table>
        <thead>
        <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Age</th>
            <th>Belt</th>
            <th></th>
        </tr>
        </thead>
        <tbody>
        {#each people as person (person.id)}
            <tr>
                <td>{person.id}</td>
                <td>{person.name}</td>
                <td>{person.age}</td>
                <td>{person.beltColor}</td>
                <td>
                    <button on:click={(e) => handleClick(e, person.id)}>Delete</button>
                </td>
            </tr>
        {/each}
        </tbody>
    </table>
</main>

<style>
    main {
        text-align: center;
        padding: 1em;
        max-width: 340px;
        margin: 0 auto;
    }

    h1 {
        color: #ff3e00;
        text-transform: uppercase;
        font-size: 4em;
        font-weight: 100;
    }

    table {
        width: 100%;
    }

    @media (min-width: 640px) {
        main {
            max-width: none;
        }
    }
</style>
