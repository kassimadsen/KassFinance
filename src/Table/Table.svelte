<script>
  let columns = ["Expense", "Reason", "Date"];
  let data = [["$1400", "Macbook", "8/6/2024"]];
  let newRow = [...columns];

  function addRow() {
    data = [...data, [...newRow]];
    newRow = columns;
  }

  function deleteRow(rowToBeDeleted) {
    data = data.filter((row) => row != rowToBeDeleted);
  }
</script>

<table>
  <tr>
    {#each columns as column}
      <th>{column}</th>
    {/each}
  </tr>

  {#each data as row}
    <tr>
      {#each row as cell}
        <td contenteditable="true" bind:innerHTML={cell} />
      {/each}
      <button on:click={() => deleteRow(row)}> X </button>
    </tr>
  {/each}

  <tr class="new">
    {#each newRow as column}
      <td contenteditable="true" bind:innerHTML={column} />
    {/each}
    <button on:click={addRow}> add </button>
  </tr>
</table>

<style>
  .new {
    color: grey;
  }
  .new td:focus {
    color: black;
  }
</style>
