<script>
  import { fly } from "svelte/transition";
  import OrderedItem from "$lib/menuPg/OrderedItem.svelte";
  import { menuItems } from "./../../store";
  $: menu = $menuItems;
  import MenuBox from "$lib/menuPg/MenuBox.svelte";
  import PicknParcel from "../../lib/menuPg/PicknParcel.svelte";
  let x = 0;
  let handleData = (ent) => {
    let item = ent.detail;
    menuItems.update((u) =>
      u.filter((i) =>
        i.smallItems.filter((j) => {
          if (j.name === item.name) {
            j.qnt += 1;
            j.prize = j.oldprize * j.qnt;
          }
        })
      )
    );
  };
  let updateFirst = (ent) => {
    let item = ent.detail;
    menuItems.update((u) =>
      u.filter((i) =>
        i.smallItems.filter((j) => {
          if (j.name === item.name) {
            j.visible = true;
            j.qnt += 1;
          }
        })
      )
    );
  };

  let decr = (ent) => {
    let item = ent.detail;
    menuItems.update((u) =>
      u.filter((i) =>
        i.smallItems.filter((j) => {
          if (j.name === item.name) {
            j.qnt -= 1;
          }
        })
      )
    );
  };
  let realVisible = 1;
  setTimeout(() => {
    realVisible = 0;
  }, 800);
</script>

<svelte:window bind:innerWidth={x} />

<main class="relative">
  <div class={x > 700 ? "parent" : "flex flex-col-reverse"}>
    <div class="div1 flex flex-wrap md:px-20 md:my-10 mt-5 md:mt-0 justify-center">
      {#each menu as mni}
        <!-- svelte-ignore missing-declaration -->
        <MenuBox
          title={mni.title}
          smallItems={mni.smallItems}
          on:mint={(ent) => handleData(ent)}
          on:first={(ent) => updateFirst(ent)}
          on:decr={(ent) => decr(ent)}
        />
      {/each}
    </div>
    {#if realVisible === 0 && x > 800}
      <div
        class="div2 bg-gradient-to-b border-l-2 border-gray-800 border-t-2 fixed top-14 right-0 from-emerald-300 to-white flex flex-col w-2/6 h-full"
        in:fly={{ y: 200, duration: 2000 }}
      >
        <OrderedItem />
        <PicknParcel />
      </div>
    {:else}
      <div
        class="div2 bg-gradient-to-b border-gray-800  from-emerald-300 to-white flex flex-col "
        in:fly={{ y: 200, duration: 2000 }}
      >
        <OrderedItem />
        <PicknParcel />
      </div>
    {/if}
  </div>
</main>

<style>
  .parent {
    display: grid;
    grid-template-columns: repeat(7, 1fr);
    grid-template-rows: repeat(5, 1fr);
    grid-column-gap: 0px;
    grid-row-gap: 0px;
  }

  .div1 {
    grid-area: 1 / 1 / 6 / 6;
  }
  .div2 {
    grid-area: 1 / 6 / 6 / 8;
  }
</style>
