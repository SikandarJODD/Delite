<script>
  import { availNum } from "../../store";
</script>

<main>
  <h2>Pre Order</h2>
  Seat No :<input type="text" bind:value={$availNum} disabled />
</main>
<style>
    main{
        margin-top: 30px;
    }
</style>
