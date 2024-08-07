<script>
  import { Table, TableBody, TableBodyCell, TableBodyRow, TableHead, TableHeadCell, TableSearch } from 'flowbite-svelte';
  let searchTerm = '';
  let items = [
    { expense: '1200', reason: 'Toyota', date: '8/7/2024' },
    { expense: '2', reason: 'Ford', date: '8/7/2024' },
  ];
  $: filteredItems = items.filter((item) => item.expense.toLowerCase().indexOf(searchTerm.toLowerCase()) !== -1 || item.reason.toLowerCase().indexOf(searchTerm.toLowerCase()) !== -1 || item.date.toLowerCase().indexOf(searchTerm.toLowerCase()) !== -1);
</script>

<TableSearch placeholder="Search" hoverable={true} bind:inputValue={searchTerm}>
  <Table hoverable={true}>
    <TableHead>
      <TableHeadCell>Expense</TableHeadCell>
      <TableHeadCell>Reason</TableHeadCell>
      <TableHeadCell>Date</TableHeadCell>
      <TableHeadCell>
        <span class="sr-only">Edit</span>
      </TableHeadCell>
    </TableHead>
    <TableBody tableBodyClass="divide-y">
      {#each filteredItems as item}
        <TableBodyRow>
          <TableBodyCell>${item.expense}</TableBodyCell>
          <TableBodyCell>{item.reason}</TableBodyCell>
          <TableBodyCell>{item.date}</TableBodyCell>
          <TableBodyCell>
            <a href="/tables" class="font-medium text-primary-600 hover:underline dark:text-primary-500">Edit</a>
          </TableBodyCell>
        </TableBodyRow>
      {/each}
    </TableBody>
    <tfoot>
      <tr class="font-semibold text-gray-900 dark:text-white">
        <th scope="row" class="py-3 px-6 text-base">Total</th>
        <td class="py-3 px-6">3</td>
        <td class="py-3 px-6">21,000</td>
      </tr>
    </tfoot>
  </Table>
</TableSearch>