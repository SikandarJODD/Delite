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
  <PersonD />
  <div class="text-center">
    <Stat />
  </div>
</main>
