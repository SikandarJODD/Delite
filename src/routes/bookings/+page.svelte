<script>
  import BookSeat from "$lib/bookingPage/BookSeat.svelte";
  let x = 0;
  import Available from "$lib/bookingPage/Available.svelte";
</script>

<svelte:window bind:innerWidth={x} />
<main class="md:px-24 text-center">
  {#if x > 700}
    <div class="parent">
      <div class="div1">
        <Available />
      </div>
      <div class="div2">
        <BookSeat />
      </div>
    </div>
    <!-- content here -->
  {/if}
</main>

<style>
  .parent {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    grid-template-rows: 1fr;
    grid-column-gap: 20px;
    grid-row-gap: 20px;
  }

  .div1 {
    grid-area: 1 / 1 / 2 / 2;
  }
  .div2 {
    grid-area: 1 / 2 / 2 / 3;
  }
</style>
