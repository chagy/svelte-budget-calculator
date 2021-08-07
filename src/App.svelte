<script>
  import { setContext } from "svelte";
  import Navbar from "./Navbar.svelte";
  import ExpensesList from "./ExpensesList.svelte";
  import Totals from "./Totals.svelte";
  import ExpenseForm from "./ExpenseForm.svelte";
  import expensesData from "./expenses";

  let expenses = [...expensesData];

  $: total = expenses.reduce((acc, curr) => {
    return (acc += curr.amount);
  }, 0);

  function removeExpense(id) {
    expenses = expenses.filter((item) => item.id !== id);
  }

  function clearExpenses() {
    expenses = [];
  }

  setContext("remove", removeExpense);
</script>

<Navbar />

<main class="content">
  <ExpenseForm />
  <Totals title="total expenses" {total} />
  <ExpensesList {expenses} />
  <button
    type="button"
    class="btn btn-primary btn-block"
    on:click={clearExpenses}
  >
    clear expenses
  </button>
</main>
