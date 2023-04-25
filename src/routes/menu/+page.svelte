<script>
  import { menuItems } from "./../../store";
  $: menu = $menuItems;
  $: console.log(menu);
  import MenuBox from "$lib/menuPg/MenuBox.svelte";

  let x = 0;
  // create Restaurent menu data with name price and quantity
  let menu = [
    { name: "Burger", price: 100, quantity: 0 },
    { name: "Pizza", price: 200, quantity: 0 },
    { name: "Sandwich", price: 50, quantity: 0 },
    { name: "Pasta", price: 150, quantity: 0 },
    { name: "Noodles", price: 100, quantity: 0 },
    { name: "Coke", price: 50, quantity: 0 },
    { name: "Fries", price: 50, quantity: 0 },
    { name: "Ice Cream", price: 100, quantity: 0 },
    { name: "Cake", price: 150, quantity: 0 },
    { name: "Milkshake", price: 100, quantity: 0 },
  ];

  let total = 0;
  let totalItems = 0;
  let cart = [];
  let cartTotal = 0;
  let cartTotalItems = 0;

  function addToCart(item) {
    let index = cart.findIndex((i) => i.name === item.name);
    if (index === -1) {
      cart.push(item);
      cartTotal += item.price;
      cartTotalItems += 1;
    } else {
      cart[index].quantity += 1;
      cartTotal += item.price;
      cartTotalItems += 1;
    }
  }

  function removeFromCart(item) {
    let index = cart.findIndex((i) => i.name === item.name);
    if (index === -1) {
      return;
    } else {
      if (cart[index].quantity === 1) {
        cart.splice(index, 1);
        cartTotal -= item.price;
        cartTotalItems -= 1;
      } else {
        cart[index].quantity -= 1;
        cartTotal -= item.price;
        cartTotalItems -= 1;
      }
    }
  }

  function clearCart() {
    cart = [];
    cartTotal = 0;
    cartTotalItems = 0;
  }
</script>

<svelte:window bind:innerWidth={x} />

<main>
  <div class={x > 700 ? "parent" : "flex flex-col-reverse"}>
    <div class="div1 flex flex-wrap">
      {#each menu as mni}
        <MenuBox title={mni.title} smallItems={mni.smallItems} />
      {/each}
    </div>
    <div class="div2 bg-orange-400">B</div>
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

  .div1 { grid-area: 1 / 1 / 6 / 6; }
.div2 { grid-area: 1 / 6 / 6 / 8; }
</style>
