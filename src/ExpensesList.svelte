<script>
  import Title from "./Title.svelte";
  import Expense from "./Expense.svelte";
  import { fly } from "svelte/transition";
  import { flip } from "svelte/animate";

  export let expenses = [];
</script>

<style>
  h2 {
    text-transform: capitalize;
  }
</style>

<section>
  <Title title="Expense list" />
  <ul>
    {#each expenses as expense, index (expense.id)}
      <div
        in:fly={{ y: 200, delay: (index + 1) * 500 }}
        out:fly={{ y: -200 }}
        animate:flip={{ duration: 500}}>
        <Expense {...expense} />
      </div>
    {:else}
      <h2>No expenses added to the list...</h2>
    {/each}
  </ul>
</section>
