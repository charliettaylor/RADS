<script lang="ts">
  export let name;
  export let teams: { [key: string]: number };
  // make a copy so it doesn't delete og object
  teams = Object.assign({}, teams);
  delete teams[name];

  const state = { "1": "win", "0": "tie", "-1": "lose" };
</script>

<table>
  <th>Team: {name}</th>
  <tbody>
    {#each Object.entries(teams) as team}
      <tr class={state[team[1]]}>{team[0]}</tr>
    {/each}
  </tbody>
</table>

<style>
  th,
  tr {
    display: flex;
    justify-content: center;
    color: white;
  }

  th {
    border-radius: 0.25rem;
    background-color: ivory;
    color: var(--background);
  }

  tr {
    border-radius: 0.25rem;
    margin-top: 0.25rem;
  }

  .win {
    background-color: var(--correct);
    color: var(--background);
  }

  .lose {
    background-color: var(--wrong);
  }

  .tie {
    background-color: darkgray;
    color: var(--background);
  }
</style>
