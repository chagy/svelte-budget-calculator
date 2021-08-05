<script>
  import SectionTitle from "./Title.svelte";
  import Expense from "./Expense.svelte";
  import App from "./App.svelte";

  export let expenses = [];
</script>

<section>
  <SectionTitle title="expense list" />
  <ul>
    {#each expenses as expense, index}
      <Expense {...expense} />
    {:else}
      <h2>On Data</h2>
    {/each}
  </ul>
</section>

<style>
  h2 {
    text-transform: capitalize;
  }
</style>
