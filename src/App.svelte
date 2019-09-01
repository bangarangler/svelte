<script>
  import ContactCard from './ContactCard.svelte';

  let userName = 'Jon';
  let jobTitle = '';
  let image = '';
  let description = '';
  let formState = "empty";

  function addContact() {
    if (userName.trim().length == 0 || jobTitle.trim().length == 0 ||
      image.trim().length == 0 || description.trim().length == 0) {
      formState = 'invalid';
      return;
    }
    formState = "done";
  }
</script>

<style>
  #form {
    width: 30rem;
    max-width: 100%;
  }
</style>

<div id="form">
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
</div>

<button on:click={addContact}>Add Contact Card</button>

{#if formState === 'done'}
<ContactCard
  {userName}
  {jobTitle}
  {description}
  {image}
/>
{:else if formState === 'invalid'}
<p>Invalid input.</p>
{:else}
  <p>Please enter some data and hit the button</p>
{/if}
