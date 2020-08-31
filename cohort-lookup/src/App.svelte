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
    max-width: 240px;
    margin: 0 auto;
  }

  span {
	  color: green;
		
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<svelte:head>
  <title>Cohort Lookup</title>
</svelte:head>

<main>
  <h1>Hello Stuy!</h1>
  <input type="text" placeholder="Your OSIS here" bind:value={query} />
  {#if lookupResult}
    <p>Your group is: <span>{lookupResult}</span></p>
  {:else}
    <p class="warning">OSIS not found</p>
  {/if}
</main>
