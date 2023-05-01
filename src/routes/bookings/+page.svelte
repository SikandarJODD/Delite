<script>
  import PlaceBook from "./../../lib/bookingPage/PlaceBook.svelte";
  import BookSeat from "$lib/bookingPage/BookSeat.svelte";
  let x = 0;
  import Available from "$lib/bookingPage/Available.svelte";
  import fastFood from "$lib/fastfood.png";
</script>

<svelte:head>
  <title>Delite Restaurant | Booking 🧀</title>
  <link rel="shortcut icon" href={fastFood} type="image/x-icon" />
  <meta name="title" content="Delite Restaurant" />
  <meta name="description" content="Delite Restaurant" />
  <meta property="og:image" content={fastFood} />
  <meta property="twitter:image" content={fastFood} />
  <meta property="twitter:title" content="Delite Restaurant" />
  <meta property="twitter:description" content="Delite Restaurant" />
  <meta name="keywords" content="Delite, Restaurant, Services, Food" />
  <meta name="author" content="Saloni Maheshwari" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta property="og:title" content="Delite Restaurant" />
  <meta property="og:type" content="website" />
  <meta property="og:url" content="https://delite-zeta.vercel.app/" />
</svelte:head>
<svelte:window bind:innerWidth={x} />
<main class="md:px-24 text-center">
  {#if x > 700}
    <div class="parent">
      <div class="div1">
        <Available />
      </div>
      <div class="div2">
        <BookSeat />
        <PlaceBook />
      </div>
    </div>
  {:else}
    <div>
      <BookSeat />
      <PlaceBook />
    </div>
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
