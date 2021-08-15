<script>
  // import { onDestroy, onMount, beforeUpdate, afterUpdate } from "svelte";

  // onMount(() => {
  //   console.log("form has onMount");
  // });

  // beforeUpdate(() => {
  //   console.log("form has beforeUpdate");
  // });

  // afterUpdate(() => {
  //   console.log("form has afterUpdate");
  // });

  // onDestroy(() => {
  //   console.log("form has onDestroy");
  // });

  import Title from "./Title.svelte";

  export let name = "";
  export let amount = null;
  export let addExpense;
  export let isEditing;
  export let editExpense;
  export let hideForm;
  // $: console.log({ name, amount });

  $: isEmpty = !name || !amount;

  function handleSubmit() {
    if (isEditing) {
      editExpense({ name, amount });
    } else {
      addExpense({ name, amount });
    }

    name = "";
    amount = null;

    hideForm();
  }
</script>

<section class="form">
  <Title title="add expense" />
  <form class="expense-form" on:submit|preventDefault={handleSubmit}>
    <div class="form-control">
      <label for="name">Name</label>
      <input type="text" name="name" id="name" bind:value={name} />
    </div>
    <div class="form-control">
      <label for="amount">Amount</label>
      <input type="text" name="amount" id="amount" bind:value={amount} />
    </div>
    {#if isEmpty}
      <p class="form-empty">plase fill out all from fields</p>
    {/if}
    <button
      type="submit"
      class="btn btn-block"
      class:disabled={isEmpty}
      disabled={isEmpty}
    >
      {#if isEditing} edit expense {:else} add expense {/if}
    </button>
    <button class="close-btn" on:click={hideForm}>
      <i class="fas fa-times" />
      close
    </button>
  </form>
</section>
