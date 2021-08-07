<script>
  import Title from "./Title.svelte";

  let name = "";
  let amount = null;

  $: console.log({ name, amount });
</script>

<section class="form">
  <Title title="add expense" />
  <form class="expense-form">
    <div class="form-control">
      <label for="name">Name</label>
      <input type="text" name="name" id="name" bind:value={name} />
    </div>
    <div class="form-control">
      <label for="amount">Amount</label>
      <input type="text" name="amount" id="amount" bind:value={amount} />
    </div>
    <p class="form-empty">plase fill out all from fields</p>

    <button type="submit" class="btn btn-block"> add expense </button>
    <button class="close-btn">
      <i class="fas fa-times" />
      close
    </button>
  </form>
</section>
