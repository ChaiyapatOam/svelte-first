<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();
  export let name;
  export let points;
  let showControl = false;
  const addPoint = () => (points += 1);
  const removePoint = () => (points += 1);
  const toggleControl = () => (showControl = !showControl);
  const deletePlayer = () => {
    dispatch("deleteplayer", name);
  };
</script>

<div class="card">
  <h1>{name}</h1>
  <h2>Point = {points}</h2>
  {#if !showControl}
    <button on:click={toggleControl}>showControl</button>
  {/if}
  {#if showControl}
    <button class="btn btn-primary" on:click={addPoint}>+1</button>
    <button class="btn btn-warning" on:click={removePoint}>-1</button> <br />
    <button class="btn btn-danger" on:click={deletePlayer}
      >Delete this Player</button
    > <br />
    <input type="number" bind:value={points} />
  {/if}
</div>

<style>
</style>
