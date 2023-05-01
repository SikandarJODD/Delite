<script>
  import OrCode from "$lib/QrCode.jpeg";
  import supabase from "$lib/db";
  import { totalPrize, orderedItems } from "../../store";
  console.log($orderedItems, $totalPrize, "bop");

  let name = "";
  let numofCustomer = 0;

  let bookTable = async () => {
    if (name.length > 0 && numofCustomer !== 0) {
      const { data, error } = await supabase.from("bookingData").insert([
        {
          name: name,
          customer: numofCustomer,
          foodItems: JSON.stringify($orderedItems),
          foodTotal: $totalPrize,
        },
      ]);
    } else {
      alert("Please fill all the fields");
    }
  };
</script>

<main
  class=" flex flex-col my-10 border-2 w-72 md:w-[500px] md:justify-between border-gray-900 rounded-lg p-5 bg-slate-200 mx-10"
>
  <form class="text-left ml-3">
    <div class="my-3">
      <label for="name">
        Name :
        <input
          required
          type="text"
          placeholder="Full Name"
          class="input input-bordered input-accent w-44 max-w-xs"
          id="name"
          bind:value={name}
        />
      </label>
    </div>
    <div class="my-3">
      <label for="No.of customers">
        No.of customers :
        <input
          required
          type="text"
          placeholder="Type here"
          class="input input-bordered input-accent w-40 max-w-xs"
          id="No.of customers"
          bind:value={numofCustomer}
        />
      </label>
    </div>
  </form>
  <div>
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <form class="mt-5" on:click|preventDefault={bookTable}>
      <script
        src="https://checkout.razorpay.com/v1/payment-button.js"
        data-payment_button_id="pl_LkVt72J6TCpvVB"
        async
      >
      </script>
    </form>
  </div>
  <!-- <div> -->
  <!-- <img src={OrCode} alt="" class="h-[400px]" /> -->
  <!-- <button class="btn btn-outline-success"
      ><a href="https://rzp.io/i/hZQ9M0p7Kd">Payment</a></button
    > -->
  <!-- </div> -->
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
