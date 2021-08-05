<script>
  import Navbar from "./Navbar.svelte";
  import ExpensesList from "./ExpensesList.svelte";
  import expensesData from "./expenses";

  let expenses = [...expensesData];
</script>

<Navbar />

<main class="content">
  <ExpensesList {expenses} />
</main>
