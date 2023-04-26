<script>
  let x = 0;
  import { availNum } from "../../store";
</script>

<svelte:window bind:innerWidth={x} />
<main>
  <h2>Pre Order</h2>
  <div>
    <div class="btn-group my-3">
      <input
        type="radio"
        on:click={() => availNum.set(2)}
        name="options"
        data-title="2"
        class="btn bg-base-100"
        checked
      />
      <input
        type="radio"
        on:click={() => availNum.set(5)}
        name="options"
        data-title="5"
        class="btn bg-base-100"
      />
      <input
        type="radio"
        on:click={() => availNum.set(11)}
        name="options"
        data-title="11"
        class="btn bg-base-100"
      />
      <input
        type="radio"
        on:click={() => availNum.set(13)}
        name="options"
        data-title="13"
        class="btn bg-base-100"
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
