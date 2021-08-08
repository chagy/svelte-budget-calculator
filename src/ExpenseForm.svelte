<script>
  import Title from "./Title.svelte";

  let name = "";
  let amount = null;

  // $: console.log({ name, amount });

  $: isEmpty = !name || !amount;

  function handleSubmit() {
    // e.preventDefault();
    console.log(name, amount);
    name = "";
    amount = null;
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
      add expense
    </button>
    <button class="close-btn">
      <i class="fas fa-times" />
      close
    </button>
  </form>
</section>
