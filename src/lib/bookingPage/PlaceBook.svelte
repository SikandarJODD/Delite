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
  class=" flex flex-col h-[350px] md:h-[250px] my-10 border-2 w-72 md:w-[500px] md:justify-between border-gray-900 rounded-lg p-5 bg-slate-200 mx-10"
>
  <form class="text-left ml-3">
    <div class="my-3">
      <label for="name">
        Name :
        <input
          required
          type="text"
          placeholder="Full Name"
          class="input input-bordered input-accent w-48 max-w-xs"
          id="name"
          bind:value={name}
        />
      </label>
    </div>
    <div class="my-3 mintV">
      <label for="No.of customers">
        No.of customers :
        <input
          required
          type="text"
          placeholder="Type here"
          class="input input-bordered input-accent w-48 max-w-xs"
          id="No.of customers"
          bind:value={numofCustomer}
        />
      </label>
    </div>
  </form>
  <div class="mt-5" on:click={bookTable}>
    <form>
      <script
        src="https://checkout.razorpay.com/v1/payment-button.js"
        data-payment_button_id="pl_LkVt72J6TCpvVB"
        async
      >
      </script>
    </form>
  </div>
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
  .mintV{
    visibility: visible !important;
  }
</style>
