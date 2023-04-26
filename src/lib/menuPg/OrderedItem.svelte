<script>
  import { menuItems } from "./../../store";
  $: menuk = $menuItems;
  $: mint = menuk.map((item) => {
    return {
      smallItems: item.smallItems.filter((i) => i.qnt > 0),
    };
  });
  $: kitu = mint.filter((item) => {
    return item.smallItems.length > 0 ? item.smallItems : null;
  });
  $: total = kitu
    .map((item) => {
      return item.smallItems.map((i) => i.prize);
    })
    .flat()
    .reduce((a, b) => a + b, 0);

  let smallItems = [
    {
      name: "Pav Bhaji",
      qnt: 0,
      veg: true,
      visible: false,
      prize: 110,
    },
    {
      name: "Jain Pav Bhaji",
      qnt: 0,
      veg: true,
      visible: false,
      prize: 90,
    },
    {
      name: "Cheese Pav Bhaji",
      qnt: 0,
      veg: true,
      visible: false,
      prize: 120,
    },
    {
      name: "Toast Pav Bhaji",
      qnt: 0,
      veg: true,
      visible: false,
      prize: 130,
    },
  ];
</script>

<main class=" h-fit mt-5 p-4 m-4 rounded-lg border-2 border-orange-500">
  <h2 class="text-2xl font-bold">Ordered Items</h2>
  <ul class="list-decimal ml-5">
    {#each kitu as item}
      {#each item.smallItems as item}
        <li class="text-lg">
          {item.name} - {item.qnt} - ₹{item.prize}
        </li>
      {/each}
    {/each}
  </ul>
  <span class="text-xl font-bold text-sky-500">Total : ₹{total}</span>

  <div class="flex justify-center flex-col md:flex-row">
    <button class="btn btn-outline btn-accent ca p-2 m-2"> Booking </button>
  </div>
</main>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@500&display=swap");
  h2 {
    font-family: "Montserrat", sans-serif;
  }
</style>
