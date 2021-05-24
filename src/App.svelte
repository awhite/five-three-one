<script>
  import { onMount } from "svelte";
  let orm = 100;

  let input = null;

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

  const headings = ["Week", "Set 1", "Set 2", "Set 3"];

  onMount(() => {
    input.focus();
  });
</script>

<main>
  <h1>5/3/1 Calculator</h1>

  <div class="flex flex-col border rounded-lg items-center p-8">
    <div class="mb-4">
      <label for="orm">One-Rep Max</label>
      <input
        id="orm"
        class="px-3 py-2 ml-2 mb-4 border dark:bg-gray-700"
        type="number"
        bind:value={orm}
        bind:this={input}
      />
    </div>

    <table>
      <tr class="border">
        {#each headings as heading}
          <th>{heading}</th>
        {/each}
      </tr>
      {#each data as week, i}
        <tr class="border mt-2">
          <td>{i + 1}</td>
          {#each week as set}
            <td>{parseInt(set)}</td>
          {/each}
        </tr>
      {/each}
    </table>
  </div>
</main>

<style>
  td,
  th {
    @apply border p-4;
  }

  main {
    @apply text-2xl max-w-lg m-auto items-center p-8 text-center;
  }

  h1 {
    @apply text-4xl mb-6 font-semibold;
  }

  input[type="number"] {
    width: 3em;
    box-sizing: content-box;
  }
</style>
