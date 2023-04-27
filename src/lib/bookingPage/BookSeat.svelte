<script>
  let x = 0;
  import { availNum } from "../../store";
  $: scoops = $availNum;
  $: console.log(scoops);
</script>

<svelte:window bind:innerWidth={x} />
<main>
  <h2>Pre Order</h2>
  <div>
    <div class="btn-group my-3">
      <input
        type="radio"
        on:click={() => {
          availNum.set(2);
        }}
        value="2"
        name="options"
        data-title="2"
        class="btn bg-base-100 hover:bg-green-200"
      />
      <input
        type="radio"
        on:click={() => {
          availNum.set(5);
        }}
        name="options"
        data-title="5"
        value="5"
        class="btn bg-base-100 hover:bg-green-200"
      />
      <input
        type="radio"
        on:click={() => availNum.set(11)}
        name="options"
        value="11"
        data-title="11"
        class="btn bg-base-100 hover:bg-green-200"
        bind:group={scoops}
      />
      <input
        type="radio"
        on:click={() => availNum.set(13)}
        name="options"
        data-title="13"
        value="13"
        class="btn bg-base-100 hover:bg-green-200"
        bind:group={scoops}
      />
    </div>
  </div>
  <form>
    <label for="seatno">
      Seat No :
      <input
        type="text"
        class="input w-20 input-bordered input-primary max-w-xs"
        id="seatno"
        disabled
        bind:value={$availNum}
      />
    </label>
  </form>
</main>

<style>
  main {
    margin-top: 30px;
  }
  input {
    color: rgb(1, 1, 62);
    font-size: 20px;
    font-weight: bold;
  }
</style>
