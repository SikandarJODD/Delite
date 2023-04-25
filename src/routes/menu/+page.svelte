<script>
  import OrderedItem from "$lib/menuPg/OrderedItem.svelte";
  import { menuItems } from "./../../store";
  $: menu = $menuItems;
  import MenuBox from "$lib/menuPg/MenuBox.svelte";
  import PicknParcel from "../../lib/menuPg/PicknParcel.svelte";
  let x = 0;
  let handleData = (ent) => {
    console.log("hello", ent.detail);
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
    console.log("hello", ent.detail);
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
    console.log("hello", ent.detail);
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
</script>

<svelte:window bind:innerWidth={x} />

<main>
  <div class={x > 700 ? "parent" : "flex flex-col-reverse"}>
    <div class="div1 flex flex-wrap px-20 my-10">
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
    <div class="div2 bg-yellow-100 flex flex-col ">
      <OrderedItem />
      <PicknParcel />
    </div>
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
