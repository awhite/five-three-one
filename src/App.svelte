<script>
  let orm = 100;
  $: max = orm * 0.9;
  $: p65 = max * 0.65;
  $: p70 = max * 0.7;
  $: p75 = max * 0.75;
  $: p80 = max * 0.8;
  $: p85 = max * 0.85;
  $: p90 = max * 0.9;
  $: p95 = max * 0.95;

  $: data = [
    [p65, p75, p85],
    [p70, p80, p90],
    [p75, p85, p95],
  ];
</script>

<main>
  <input type="number" bind:value={orm} />

  <table>
    <tr>
      <th>Week</th>
      <th>Set 1</th>
      <th>Set 2</th>
      <th>Set 3</th>
    </tr>
    {#each data as week, i}
      <tr>
        <td>{i + 1}</td>
        {#each week as set}
          <td>{set.toFixed(2)}</td>
        {/each}
      </tr>
    {/each}
  </table>
</main>

<style>
</style>
