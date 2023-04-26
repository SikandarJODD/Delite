<script>
  import Forbidden from "$lib/forbidden.png";
  import Available from "$lib/available.png";
</script>

<main>
  <div class="parent">
    <div class="div1">1</div>
    <div class="div2 bgGreen">
      <img src={Available} alt="Avail" />
      <span>2</span>
    </div>
    <div class="div3">3</div>
    <div class="div4">4</div>
    <div class="div5 bgGreen">
      <img src={Available} alt="Avail" />
      <span>5</span>
    </div>
    <div class="div6">6</div>
    <div class="div7">7</div>
    <div class="div8">8</div>
    <div class="div9">9</div>
    <div class="div10">10</div>
    <div class="div11 bgGreen">
      <img src={Available} alt="Avail" />
      <span>11</span>
    </div>
    <div class="div12">12</div>
    <div class="div13 bgGreen">
      <img src={Available} alt="Avail" />
      <span>13</span>
    </div>
    <div class="div14">14</div>
    <div class="div15">15</div>
    <div class="div16">16</div>
  </div>
</main>

<style>
  .bgGreen {
    background: lightgreen !important;
    border: 2px solid rgb(1, 22, 50);
  }
  .parent {
    width: 700px;
    /* background: rgb(242, 242, 242); */
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-template-rows: repeat(4, 1fr);
    grid-column-gap: 20px;
    grid-row-gap: 20px;
    margin: 30px 0;
  }
  .parent div {
    height: 130px;
    width: 110px;
    background: rgb(199, 235, 248);
    padding: 15px;
    border-radius: 10px;
  }
  .parent div span {
    font-size: 18px;
    font-weight: bold;
    color: rgb(0, 27, 67);
  }

  .div1 {
    grid-area: 1 / 1 / 2 / 2;
  }
  .div2 {
    grid-area: 1 / 2 / 2 / 3;
  }
  .div3 {
    grid-area: 1 / 3 / 2 / 4;
  }
  .div4 {
    grid-area: 1 / 4 / 2 / 5;
  }
  .div5 {
    grid-area: 2 / 1 / 3 / 2;
  }
  .div6 {
    grid-area: 2 / 2 / 3 / 3;
  }
  .div7 {
    grid-area: 2 / 3 / 3 / 4;
  }
  .div8 {
    grid-area: 2 / 4 / 3 / 5;
  }
  .div9 {
    grid-area: 3 / 1 / 4 / 2;
  }
  .div10 {
    grid-area: 3 / 2 / 4 / 3;
  }
  .div11 {
    grid-area: 3 / 3 / 4 / 4;
  }
  .div12 {
    grid-area: 3 / 4 / 4 / 5;
  }
  .div13 {
    grid-area: 4 / 1 / 5 / 2;
  }
  .div14 {
    grid-area: 4 / 2 / 5 / 3;
  }
  .div15 {
    grid-area: 4 / 3 / 5 / 4;
  }
  .div16 {
    grid-area: 4 / 4 / 5 / 5;
  }
</style>
