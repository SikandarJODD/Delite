<script>
  import { createEventDispatcher } from "svelte";
  export let title = "Basmati Khazana";
  export let smallItems;
  const dispatch = createEventDispatcher();
  let handleData = (item) => {
    dispatch("mint", item);
  };
  let updatefirst = (item) => {
    dispatch("first", item);
  };
  let decr = (item) => {
    dispatch("decr", item);
  };

  let incr = (item) => {
    dispatch("incr", item);
  };
</script>

<main class="box border rounded-2xl hover:shadow-xl hover:shadow-gray-400 transition-all duration-150 hover:bg-yellow-400 border-gray-900 m-3 p-2 md:w-[380px]">
  <h3
    class="bxtitle font-bold text-md border-2 border-gray-900 w-fit px-2 rounded-md bg-[#a3fb91] m-2"
  >
    {title}
  </h3>
  <div class="mx-10">
    {#each smallItems as item}
      <li class="items-center flex my-1 cursor-pointer">
        <!-- svelte-ignore a11y-click-events-have-key-events -->
        <span on:click={updatefirst(item)}>{item.name}</span>
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
          <!-- svelte-ignore missing-declaration -->
          <button
            on:click={handleData(item)}
            class="border-2 pb-1 border-gray-800 px-1 rounded-md mx-2">+</button
          >
          <span  >{item.qnt}</span>
          <button
            on:click={decr(item)}
            class="border-2 text-center border-gray-800 px-1 pb-1 rounded-md mx-2">-</button
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
