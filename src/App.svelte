<script>
  import Navbar from "./Navbar.svelte";
  import Player from "./Player.svelte";
  import AddPlayer from "./AddPlayer.svelte";
  let players = [
    {
      name: "Kabigon",
      points: 50,
    },
    {
      name: "Psyduck",
      points: 45,
    },
    {
      name: "Pikachu",
      points: 50,
    },
  ];
  const addPlayer = (e) => {
    const newPlayer = e.detail;
    players = [...players, newPlayer];
  };
  const deletePlayer = (e) => {
    players = players.filter((player) => player.name != e.detail);
  };
</script>

<Navbar />
<div class="container" />
<AddPlayer on:addplayer={addPlayer} />
{#if players.length === 0}
  <p>No Player</p>
{:else}
  {#each players as player}
    {player.name}
    <Player
      name={player.name}
      points={player.points}
      on:deleteplayer={deletePlayer}
    />
  {/each}
{/if}

<style>
</style>
