<script lang="ts">
  let query: string;

  import data from "./data";
  let idSet = new Set<string>();
  let map = new Map<string, string>();
  for (let row of data) {
    let osis = row[0];
    let cohort = row[2];
    idSet.add(osis);
    map.set(osis, cohort);
  }

  $: lookupResult = map.get(query);
</script>

<style>
  main {
    text-align: center;
    padding: 1em;
    /* max-width: 240px; */
    margin: 0 auto;
  }

  span {
    color: green;
  }

  .result {
	font-size: 2rem;
    padding: 1.5rem 2rem;
    border-radius: 0.2rem;
    margin: 0 auto;
  }

  input {
    font-family: "Roboto", sans-serif;
    color: #333;
    font-size: 1rem;
    margin: 0 auto;
    padding: 1.5rem 2rem;
    border-radius: 0.2rem;
    background-color: rgb(255, 255, 255);
    /* border: none; */
    width: 90%;
    display: block;
    /* border-bottom: 0.3rem solid black; */
    transition: all 0.3s;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }
</style>

<svelte:head>
  <title>Cohort Lookup</title>
</svelte:head>

<main>
  <h1>Hello Stuy!</h1>
  <p>Get your cohort</p>
  <input type="text" placeholder="Your OSIS here" bind:value={query} />
  <div class="result">
    {#if lookupResult}
      <code>Your group is: <span>{lookupResult}</span></code>
    {:else}
      <p>OSIS not found</p>
    {/if}
  </div>
  <p>Original spreedsheet & more descriptions <a target="_blank" href="https://tinyurl.com/Stuy-Blended">here</a></p>
</main>
