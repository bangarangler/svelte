<script>
  import ContactCard from './ContactCard.svelte';

  let userName = 'Jon';
  let jobTitle = '';
  let image = '';
  let description = '';
  let formState = "empty";
  let createdContacts = [];

  function addContact(event) {
    /*e.preventDefault();*/
    if (userName.trim().length == 0 || jobTitle.trim().length == 0 ||
      image.trim().length == 0 || description.trim().length == 0) {
      formState = 'invalid';
      return;
    }
    createdContacts = [
      ...createdContacts,
      ({
      id: Math.random(),
      userName,
      jobTitle,
      image,
      description
    })]
    formState = "done";
  }
  function deleteFirst() {
    createdContacts = createdContacts.slice(1);
  }
  function deleteLast() {
    createdContacts = createdContacts.slice(0, -1);
  }
</script>

<style>
  #form {
    width: 30rem;
    max-width: 100%;
    margin: 1rem 0;
  }
</style>

<form id="form">
  <div class="form-control">
    <label for="userName">User Name</label>
    <input type="text" bind:value="{userName}" id="userName" />
  </div>
  <div class="form-control">
    <label for="jobTitle">Job Title</label>
    <input type="text" bind:value="{jobTitle}" id="jobTitle" />
  </div>
  <div class="form-control">
    <label for="image">Image URL</label>
    <input type="text" bind:value="{image}" id="image" />
  </div>
  <div class="form-control">
    <label for="desc">Description</label>
    <textarea rows="3" bind:value="{description}" id="desc" />
  </div>
  <button type="submit" on:click|preventDefault={addContact}>Add Contact Card</button>
</form>

<button on:click={deleteFirst}>Delete First</button>
<button on:click={deleteLast}>Delete Laxt</button>


{#if formState === 'invalid'}
  <p>Invalid input.</p>
{:else}
  <p>Please enter some data and hit the button</p>
{/if}

{#each createdContacts as contact, i (contact.id)}
  <h2># {i + 1}</h2>
  <ContactCard
    userName={contact.userName}
    jobTitle={contact.jobTitle}
    description={contact.description}
    image={contact.image}
  />
{:else}
  <p>Please start adding some constacts, we found none!</p>
{/each}
