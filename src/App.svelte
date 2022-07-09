<script>
    import Modal from './Modal.svelte';
    import AddPersonForm from './AddPersonForm.svelte';

    let people = [
        {name: 'Yoshi', beltColor: 'black', age: 25, id: 1},
        {name: 'Mario', beltColor: 'orange', age: 45, id: 2},
        {name: 'Luigi', beltColor: 'brown', age: 35, id: 3},
    ];

    let showModal = false;

    const toggleModal = () => {
        showModal = !showModal;
    };

    const handleClick = (e, id) => {
        // print the event
        console.log(e);
        // delete the person from people
        people = people.filter(person => person.id !== id);
    }

    let num = 5;
</script>

{#if num > 20}
    <p>Greater than 20.</p>
{:else if num > 5}
    <p>Greater than 5.</p>
{:else}
    <p>Lower or equals to 5.</p>
{/if}

<Modal isPromo={true} {showModal} on:click={toggleModal}>
    <div slot="title">
        <h3>Add a new person</h3>
    </div>
    <AddPersonForm />
</Modal>


<main>

    <!-- Use the once modifier to prevent the toggle button to work several times -->
    <button on:click={toggleModal}>toggle modal</button>

    <h1>People</h1>
    <ul>
        {#each people as person (person.id)}
            <li>
                <h2>{person.name}</h2>
                {#if person.beltColor === 'black'}
                    <p><strong>Master Ninja!</strong></p>
                {/if}
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
