<script>
  import supabase from "$lib/db";
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
  $: tifukitu = kitu.map((e) =>
    e.smallItems.map((i) => {
      return {
        name: i.name,
        qnt: i.qnt,
        veg: i.veg,
        visible: i.visible,
        prize: i.prize,
      };
    })
  );
  $: lastString =
    tifukitu.length > 0
      ? tifukitu.map((e) => {
          return e.map((i) => {
            return `${i.name} - ${i.qnt} - ₹${i.prize}`;
          });
        })
      : " ";
  $: console.log(lastString, "bbb");
  $: total = kitu
    .map((item) => {
      return item.smallItems.map((i) => i.prize);
    })
    .flat()
    .reduce((a, b) => a + b, 0);
  /* 
    {#each kitu as item}
      {#each item.smallItems as item}
        <li class="text-lg">
          {item.name} - {item.qnt} - ₹{item.prize}
        </li>
      {/each}
    {/each}
    */
  let name = "";
  let phone = "";
  let uploadData = async () => {
    console.log(name, phone, lastString, total, tifukitu);
    const { data, error } = await supabase.from("pickParcel").insert([
      {
        name: name,
        phone: phone,
        orders: JSON.stringify(lastString),
        total: total,
      },
    ]);
  };
</script>

<main>
  <form
    class="border-2 border-gray-900 mx-4 p-5 rounded-md"
    on:submit|preventDefault={uploadData}
  >
    <label for="name"
      >Name :
      <input
        type="text"
        placeholder="Type here"
        class="input w-full max-w-xs"
        name="name"
        id="name"
        required
        bind:value={name}
      />
    </label>
    <label for="phone"
      >Phone :
      <input
        type="text"
        placeholder="Type here"
        class="input input-bordered w-full max-w-xs"
        name="phone"
        id="phone"
        required
        bind:value={phone}
      />
    </label>
    <div class="text-center">
      <button
        class="btn btn-outline border-green-600 hover:bg-emerald-500 mt-4 text-gray-700 hover:text-gray-900"
      >
        Pick & Parcel Order
      </button>
    </div>
  </form>
</main>

<style>
  input {
    margin-top: 10px;
  }
</style>
