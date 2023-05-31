<script>
  import PersonD from "$lib/AboutPg/PersonD.svelte";
  import Stat from "$lib/AboutPg/Stat.svelte";
  import fastFood from "$lib/fastfood.png";
</script>

<svelte:head>
  <title>Delite Restaurant 🧀 | About</title>
  <link rel="shortcut icon" href={fastFood} type="image/x-icon" />
  <meta name="title" content="Delite Restaurant" />
  <meta name="description" content="Delite Restaurant" />
  <meta property="og:image" content={fastFood} />
  <meta property="twitter:image" content={fastFood} />
  <meta property="twitter:title" content="Delite Restaurant" />
  <meta property="twitter:description" content="Delite Restaurant" />
  <meta name="keywords" content="Delite, Restaurant, Services, Food" />
  <meta name="author" content="Saloni Maheshwari" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <meta property="og:title" content="Delite Restaurant" />
  <meta property="og:type" content="website" />
  <meta property="og:url" content="https://delite-zeta.vercel.app/" />
</svelte:head>
<main>
  <!-- <PersonD /> -->
  <div class="bg-green-400 px-4 py-3 text-gray-900">
    <p class="text-center text-sm font-medium">
      Enjoy Delite Restaurant ❤️️
      <a
        href="https://github.com/SikandarJODD/bun"
        target="_blank"
        class="inline-block underline"
      >
        Give us Star on Github</a
      >
    </p>
  </div>

  <div class="bg-white">
    <div class="max-w-7xl mx-auto py-16 px-4 sm:px-6 lg:px-8">
      <div class="text-center">
        <div class=" rounded-full">
          <img
            src="https://media.licdn.com/dms/image/C4D03AQGP1dNhTLkZrA/profile-displayphoto-shrink_800_800/0/1662137583464?e=1691020800&v=beta&t=VsLUVmVvzVdtij0f-Qe5KjE_Vq4sYiyQ4Ov_8qkuF6w"
            alt=""
            class="rounded-full h-52 w-52 mx-auto border-2 p-2 border-green-500 hover:scale-110 transition duration-300 ease-in-out mb-4"
          />
        </div>
        <p
          class="mt-1 text-xl font-extrabold text-gray-700 sm:text-5xl sm:tracking-tight lg:text-5xl"
        >
          Developed By <span
            class="bg-clip-text text-transparent bg-gradient-to-r from-cyan-500 to-sky-600"
            >Sikandar.S.Bhide</span
          >
        </p>
        <p class="max-w-xl mt-5 mx-auto text-xl text-gray-500">
          Delite Restaurant is a web application developed using <span class="text-gray-700 font-mono bg-base-300 p-1 rounded-md"
            >Sveltekit
          </span>
          & <span class="text-gray-700 font-mono bg-base-300 p-1 rounded-md">Supabase</span>
        </p>
      </div>
    </div>
  </div>
  <div class="text-center">
    <!-- <Stat /> -->
  </div>
</main>
