<script lang="ts">
    import {
        Table,
        TableBody,
        TableBodyCell,
        TableBodyRow,
        TableHead,
        TableHeadCell
    } from "flowbite-svelte";
    import type {Item} from "../model/Item";
    export let items: Item[] = [];
</script>

<div class="p-12 w-11/12 lg:w-8/12 flex flex-col justify-center">
    <Table shadow>
        <TableHead>
            <TableHeadCell>Product ID</TableHeadCell>
            <TableHeadCell>Name</TableHeadCell>
            <TableHeadCell>Price</TableHeadCell>
        </TableHead>
        <TableBody>

            {#each items as item}
                <TableBodyRow>
                    <TableBodyCell>{item.id}</TableBodyCell>
                    <TableBodyCell>{item.name}</TableBodyCell>
                    <TableBodyCell>{item.price}</TableBodyCell>
                </TableBodyRow>
            {/each}

        </TableBody>
    </Table>

</div>
