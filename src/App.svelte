<script>
  
  import Modal from './Modal.svelte';

  let showModal = false;

  let people= [
    {name: 'Yoshi', beltColour: 'black', age: 25, id:1},
    {name: 'Mario', beltColour: 'orange', age: 35, id:2},
    {name: 'Luigi', beltColour: 'brown', age: 20, id:3}
  ];

  const openModal = () => {
    showModal = !showModal;
  }

  const handleClick = (id) => {
    //delete person from list
    people = people.filter( (person) =>person.id !== id);
  }

</script>

<Modal {showModal} message={"Hello, I am a prop value!"} on:click={openModal}/> <!-- showModal is a prop value and it is a shorthand, we do not have to specify the name if it is the same as the name of the variable -->
<main>
  <button on:click={openModal}>Open modal</button>
  {#each people as person (person.id)} <!-- person.id link the elements nder the hood with the specific element -->
    <div>
      <h4>{person.name}</h4>
      {#if person.beltColour === 'black'}
        <p><strong>MASTER NINJA</strong></p>
      {/if}
      <p>{person.age} years old, {person.beltColour} belt.</p>
      <button on:click={() => handleClick(person.id)}>Delete</button>
    </div>
  {:else}
    <p>There are no people</p>
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
