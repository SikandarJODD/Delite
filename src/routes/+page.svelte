<script>
  import ImgComp from "./../lib/components/ImgComp.svelte";
  import fastFood from "$lib/fast-food.png";
  import FineFood from "$lib/fine.png";
  import Fine2 from "$lib/fine2.png";
  import Fine3 from "$lib/fine3.png";
  import Fine4 from "$lib/fine4.png";
  import { goto } from "$app/navigation";
  import { fade, scale } from "svelte/transition";
  import Chefhat from "$lib/chef-hat.png";
  import Services from "../lib/components/Services.svelte";
  let foodImg = [
    {
      imgSrc: FineFood,
      bg: "bg-gradient-to-b from-emerald-500 to-blue-200",
    },
    {
      imgSrc: Fine2,
      bg: "from-yellow-300 to-white",
    },
    {
      imgSrc: Fine3,
      bg: "from-green-400 to-blue-200",
    },
    {
      imgSrc: Fine4,
      bg: "from-emerald-500 via-yellow-200 to-white",
    },
  ];

  let i = 0;
  setInterval(() => {
    i++;
    if (i > 3) {
      i = 0;
    }
  }, 3000);
  $: imgSrc = foodImg[i].imgSrc;
  $: bg = foodImg[i].bg;
</script>

<svelte:head>
  <title>Delite Restaurant 🧀</title>
  <link rel="shortcut icon" href={fastFood} type="image/x-icon" />
  <meta name="title" content="Delite Restaurant" />
  <meta name="description" content="Delite Restaurant" />
  <meta property="og:image" content={fastFood} />
  <meta property="twitter:image" content={fastFood} />
  <meta property="twitter:title" content="Delite Restaurant" />
  <meta property="twitter:description" content="Delite Restaurant" />
  <meta name="keywords" content="Delite, Restaurant, Services, Food" />
  <meta name="author" content="Delite Restaurant" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta property="og:title" content="Delite Restaurant" />
  <meta property="og:type" content="website" />
  <meta property="og:url" content="https://delite-zeta.vercel.app/" />
</svelte:head>
<div class="hero min-h-64 md:min-h-screen mint">
  <div class="hero-content flex-col lg:flex-row-reverse relative">
    <div class=" hidden md:stack mb-8 md:mb-0">
      <div
        class="text-center border-2 border-base-content card max-w-sm bg-gradient-to-b {bg} "
      >
        <div class="card-body">
          <!-- svelte-ignore a11y-missing-attribute -->
          {#key imgSrc}
            <img src={imgSrc} class="max-w-sm rounded-lg" in:fade />
          {/key}
        </div>
      </div>
      <div
        class="text-center border-2 border-base-content card max-w-sm bg-base-100"
      >
        <div class="card-body">
          <img src={FineFood} class="max-w-sm rounded-lg" />
        </div>
      </div>
      <div
        class="text-center border-2 border-base-content card max-w-sm bg-base-900"
      >
        <div class="card-body">
          <img src={FineFood} class="max-w-sm rounded-lg" />
        </div>
      </div>
    </div>
    <!-- svelte-ignore a11y-missing-attribute -->
    <img
      src={Chefhat}
      class=" hidden lg:flex max-w-sm rounded-lg absolute top-[-15px] left-[-15px] scale-110 -rotate-45"
    />
    <div
      class="border-2 px-5 py-5 md:py-14 md:mr-10 border-gray-900 rounded-lg md:w-3/5 shd"
    >
      <h1 class="text-3xl text-center md:text-left md:text-5xl font-bold">
        Delite Restaraunts & Services
      </h1>
      <p class="py-6 w-4/5 hidden md:flex">
        Delite Restaurant is a restaurant that offers a variety of dishes and a
        variety of services. We offer a variety of dishes from different parts
        of the India.
      </p>
      <div
        class="text-center mt-3 md:mt-0 flex flex-col md:flex-row md:text-left"
      >
        <button
          class="btn my-1 md:mx-1 md:btn-md btn-outline hover:bg-sky-400 hover:text-gray-900"
          on:click={() => {
            goto("/bookings");
          }}>Booking</button
        >
        <button
          class="btn my-1 md:mx-1 btn-outline bg-emerald-300 hover:bg-emerald-400 hover:text-gray-900"
          on:click={() => {
            goto("/bookings");
          }}>Pick Parcel</button
        >
        <button
          class="btn my-1 md:mx-1 btn-outline bg-amber-300 hover:bg-yellow-400 hover:text-gray-900"
          on:click={() => {
            goto("/menu");
          }}>Menus</button
        >
      </div>
    </div>
  </div>
</div>
<Services />
<ImgComp />

<style lang="postcss">
  /* :global(html) {
    background-color: theme(colors.gray.100);
  } */
  .shd {
    background: linear-gradient(to right, #2acffd, #0072ff);
    box-shadow: rgba(31, 243, 194, 0.496) 0px 19px 38px,
      rgba(36, 251, 32, 0.22) 0px 15px 12px;
  }
  .mint {
    background: white !important;
  }
</style>
