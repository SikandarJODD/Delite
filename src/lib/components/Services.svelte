<script>
  import Mint1 from "$lib/min1.gif";
  import Mint2 from "$lib/min2.gif";
  import Mint3 from "$lib/min3.gif";
  import Mint4 from "$lib/min4.gif";
  import Mint5 from "$lib/min5.gif";
  import Mint6 from "$lib/min6.gif";
  let serData = [
    {
      id: 1,
      md: true,
      title: "Hot & Fresh",
      desc: "Filler text is dummy text which has no meaning however looks very similar to real text.",
      icon: Mint1,
    },
    {
      id: 2,
      md: true,
      title: "Custom Booking",
      desc: "Filler text is dummy text which has no meaning however looks very similar to real text.",
      icon: Mint2,
    },
    {
      id: 3,
      md: true,
      title: "AC & Non-AC",
      desc: "Filler text is dummy text which has no meaning however looks very similar to real text.",
      icon: Mint3,
    },
    {
      id: 4,
      md: true,
      title: "Pick & Parcel",
      desc: "Filler text is dummy text which has no meaning however looks very similar to real text.",
      icon: Mint4,
    },
    {
      id: 5,
      md: false,
      title: "Auspicious Dinning",
      desc: "Filler text is dummy text which has no meaning however looks very similar to real text.",
      icon: Mint5,
    },
    {
      id: 6,
      md: false,
      title: "Wifi & Parking",
      desc: "Filler text is dummy text which has no meaning however looks very similar to real text.",
      icon: Mint6,
    },
  ];
</script>

<div class="bg-white py-6 sm:py-8 lg:py-12 md:mx-20">
  <div class="mx-auto max-w-screen-2xl px-4 md:px-8">
    <!-- text - start -->
    <div class="mb-10 md:mb-16">
      <h2
        class="mb-4 text-center text-2xl font-bold text-sky-500 md:mb-6 lg:text-5xl"
      >
        Our Services
      </h2>
    </div>
    <!-- text - end -->

    <div class="grid gap-12 sm:grid-cols-2 xl:grid-cols-3 xl:gap-12">
      <!-- feature - start -->
      {#each serData as ser}
        <div
          class="flex flex-col items-center rounded-md hover:bg-sky-300 transition-all border-2 border-transparent duration-200 hover:border-2 hover:border-gray-900 py-6"
        >
          <div
            class="mb-6 flex h-12 w-12 items-center justify-center text-white border-2 border-sky-500 md:h-14 md:w-14"
          >
            <!-- Svg  -->
            <img src={ser.icon} alt={ser.title} />
            <!-- {@html ser.icon} -->
          </div>

          <h3 class="mb-2 text-center text-lg font-semibold md:text-xl">
            {ser.title}
          </h3>
          <p class="mb-2 text-center text-gray-500">
            {ser.desc}
          </p>
        </div>
      {/each}
      <!-- feature - end -->
    </div>
  </div>
</div>
