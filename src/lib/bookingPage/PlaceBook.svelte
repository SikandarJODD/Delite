<script>
  import supabase from "$lib/db";
  import { totalPrize, orderedItems } from "../../store";
  console.log($orderedItems, $totalPrize, "bop");
  let name = "";
  let numofCustomer = 0;

  let bookTable = async () => {
    const { data, error } = await supabase.from("bookingData").insert([
      {
        name: name,
        customer: numofCustomer,
        foodItems: JSON.stringify($orderedItems),
        foodTotal: $totalPrize,
      },
    ]);
  };
</script>

<main class=" my-10 border-2 border-gray-900 rounded-lg p-5 bg-slate-200 mx-10">
  <form class="text-left ml-3" on:submit|preventDefault={bookTable}>
    <div class="my-3">
      <label for="name">
        Name :
        <input
          type="text"
          placeholder="Full Name"
          class="input input-bordered input-accent w-full max-w-xs"
          id="name"
          bind:value={name}
        />
      </label>
    </div>
    <div class="my-3">
      <label for="No.of customers">
        No.of customers :
        <input
          type="text"
          placeholder="Type here"
          class="input input-bordered input-accent w-full max-w-xs"
          id="No.of customers"
          bind:value={numofCustomer}
        />
      </label>
    </div>
    <div>
      <button class="btn btn-outline btn-primary">Book</button>
    </div>
  </form>
</main>

<style>
  label {
    font-size: 18px;
    font-weight: bold;
    color: rgb(0, 162, 255);
  }
  input {
    color: rgba(0, 19, 61, 0.84) !important;
    margin-left: 10px;
  }
</style>
