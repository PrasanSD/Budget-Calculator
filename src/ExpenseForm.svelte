<script>
  // Components
  import Title from "./Title.svelte";
  // Props
  export let addExpense;
  export let name = "";
  export let description = "";
  export let amount = null;
  export let isEditing;
  export let editExpense;
  export let hideForm;
  // Variables
  $: isEmpty = !name || !description ||!amount;

  // Functions
  function handleSubmit() {
    if (isEditing) {
      editExpense({ name, description, amount });
    } else {
      addExpense({ name, description, amount });
    }
    name = "";
    description = "";
    amount = null;
    hideForm();
  }
</script>

<section class="form">
  <Title title="Add Expense" />
  <form class="expense-form" on:submit|preventDefault={handleSubmit}>
    <div class="form-control">
      <label for="name">Name</label>
      <input type="text" id="name" bind:value={name} />
    </div>
    <div class="form-control">
      <label for="description">Description</label>
      <textarea type="text" id="description" bind:value={description} />
    </div>
    <div class="form-control">
      <label for="amount">Amount</label>
      <input type="number" id="amount" bind:value={amount} />
    </div>
    {#if isEmpty}
      <p class="form-empty">Please fill all the fields in the form...</p>
    {/if}
    <button
      type="submit"
      class="btn btn-block"
      disabled={isEmpty}
      class:disabled={isEmpty}>
      {isEditing ? 'Edit Expense' : 'Add Expense'}
    </button>
    <button type="button" class="close-btn" on:click={hideForm}>
      <i class="fas fa-times" />
      Close
    </button>
  </form>
</section>
