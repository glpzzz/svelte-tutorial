<script>
    import Modal from './Modal.svelte';
    import AddPersonForm from './AddPersonForm.svelte';

    let people = [
        {name: 'Yoshi', beltColor: 'black', age: 25, id: 1, skills: []},
        {name: 'Mario', beltColor: 'orange', age: 45, id: 2, skills: []},
        {name: 'Luigi', beltColor: 'brown', age: 35, id: 3, skills: []},
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

    const addPerson = (e) => {
        const person = e.detail;
        console.log(e, person);
        people = [person, ...people];
        showModal = false;
    }

</script>

<Modal isPromo={true} {showModal} on:click={toggleModal}>
    <div slot="title">
        <h3>Add a new person</h3>
    </div>
    <AddPersonForm on:AddPersonForm.Submit={addPerson}/>
</Modal>

<main>

    <h1>People</h1>

    <table>
        <thead>
        <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Age</th>
            <th>Belt</th>
            <th>Skills</th>
            <th>
                <!-- Use the once modifier to prevent the toggle button to work several times -->
                <button on:click={toggleModal}>New Person</button>
            </th>
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
                    {#each person.skills as skill}
                        {skill},
                    {/each}
                </td>
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

</style>
