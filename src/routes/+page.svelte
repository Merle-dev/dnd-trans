<script>
  import "../styles.css"
  import "../dices.css"
  import { onMount } from 'svelte';
  let buffs = [
    {name: "stregth", val: 0},
    {name: "dexterity", val: 0},
    {name: "constitution", val: 0},
    {name: "intelligence", val: 0},
    {name: "wisdom", val: 0},
    {name: "charisma", val: 0}
  ];
  let  dices = false;
  let dice = 0;

  function sleep(ms) {
    return new Promise((resolve) => setTimeout(resolve, ms ?? 200));
  }
  async function roll(d) {
    for(let _ = 0; _ < 30; _++) {
      await sleep(150);
      dice = Math.round(Math.random() * d);
    }
  }
</script>

<div class="main">
  <div class="t-row">
    {#each buffs as stat}
      <div class="t-box vis-element">
        <p class="stat">{stat.name}</p>
        <p class="stat_val">{stat.val}</p>
      </div>
    {/each}
    <div class="t-r-row">
      <div class="t-r-quad vis-element"><p>1</p></div>
      <div class="t-r-quad vis-element"><p>2</p></div>
      <div class="t-r-rect vis-element"><p>3</p></div>
    </div>
  </div>
  <div class="v-half v-half-container">
    <div class="v-half f-col">
      <div class="h-third vis-element"><p>4</p></div>
      <div class="h-third vis-element"><p>5</p></div>
      <div class="h-third-end vis-element"><p>6</p></div>
    </div>
    <div class="v-half f-col vis-element">
    </div>
  </div>
  <div class="v-half">
    <div class="r-top">
      <div class="r-top-quad vis-element"><p>7</p></div>
      <div class="r-top-quad vis-element"><p>8</p></div>
      <div class="r-top-rect vis-element"><p>9</p></div>
    </div>
    <div class="r-box vis-element">
      <p>Lorem ipsum dolor sit amet, qui minim labore adipisicing minim sint cillum sint consectetur cupidatat.</p>
    </div>
  </div>
</div>

<div class="dices">
  <button class="dicebuttons dicebutton" on:click={() => {dices = !dices}}><p>Dices</p></button>
  {#if dices}
        <p>{dice}</p>
    {#each [4, 6, 8, 10, 12, 20, 100] as d}
      <div>
        <button class="dicebuttons" on:click={() => roll(d)}><p>D{d}</p></button>
      </div>
    {/each}
  {/if}
</div>










<!---->
<!-- <div class="wrapper"> -->
<!--   <div class="ring"></div> -->
<!--   <div class="sun"></div> -->
<!--   <div class="planets"> -->
<!--     <div class="one"></div> -->
<!--     <div class="two"></div> -->
<!--     <div class="three"></div> -->
<!--   </div> -->
<!-- </div> -->
<!---->
<!-- <link rel="stylesheet" href="./styles.css"> -->

<style>
  :global(body) {
    margin: 0;
    background: url("./dndtrans_bg.jpg") no-repeat center center fixed;
  }
</style>

<svelte:head>
  <link href="https://fonts.googleapis.com/css2?family=Sedan:ital@0;1&display=swap" rel="stylesheet">
</svelte:head>
