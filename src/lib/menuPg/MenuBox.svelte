<script>
  export let title = "Basmati Khazana";
  export let smallItems = [
    {
      name: "Veg. Biryani",
      qnt: 0,
      veg: true,
      visible: false,
      prize: 270,
    },
    {
      name: "Veg. Hyderabadi Biryani",
      qnt: 0,
      veg: true,
      visible: false,
      prize: 270,
    },
    {
      name: "Veg. Handi Biryani",
      qnt: 0,
      veg: true,
      visible: false,
      prize: 270,
    },
    {
      name: "Cheese Biryani",
      qnt: 0,
      veg: true,
      visible: false,
      prize: 270,
    },
    {
      name: " Paneer Biryani",
      qnt: 0,
      veg: true,
      visible: false,
      prize: 270,
    },
    {
      name: "Chicken Dum Biryani",
      qnt: 0,
      veg: false,
      visible: false,
      prize: 270,
    },
    {
      name: "Kolkatta Chicken Biryani",
      qnt: 0,
      veg: false,
      visible: false,
      prize: 270,
    },
    {
      name: "Egg Biryani",
      qnt: 0,
      veg: false,
      visible: false,
      prize: 270,
    },
  ];
</script>

<main class="box border border-gray-900 m-3 p-2 md:w-[380px]">
  <h3
    class="bxtitle font-bold text-md border-2 border-gray-900 w-fit px-2 rounded-md bg-[#a3fb91] m-2"
  >
    {title}
  </h3>
  <div class="mx-10">
    {#each smallItems as item}
      <li class="items-center flex my-1 cursor-pointer">
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <span
          on:click|once={() => {
            item.visible = true;
            item.qnt += 1;
          }}>{item.name}</span
        >
        {#if item.veg}
          <span
            class="text-green-500 opacity-80 text-[8px] mx-1 mt-1 items-center"
          >
            🟢</span
          >
        {:else}
          <span
            class="text-red-500 opacity-70 text-[8px] mx-1 mt-1 items-center"
          >
            🔴</span
          >
        {/if}
        <span class="ml-auto">₹{item.prize}</span>

        {#if item.visible === true}
          <button
            on:click={() => {
              item.qnt += 1;
              item.prize = item.prize + item.prize / (item.qnt - 1);
            }}
            class="border-2 border-gray-800 px-1 rounded-md mx-2">+</button
          >
          <span>{item.qnt}</span>
          <button
            on:click={() => {
              if (item.qnt > 0) {
                item.qnt -= 1;
              }
              if (item.qnt === 0) {
                item.visible = false;
              }
            }}
            class="border-2 border-gray-800 px-1 rounded-md mx-2">-</button
          >
        {/if}
      </li>
    {/each}
  </div>
</main>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Ubuntu:wght@300&display=swap");

  .bxtitle {
    font-family: "Ubuntu", sans-serif;
  }
</style>
