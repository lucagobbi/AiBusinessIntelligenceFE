<script lang="ts">
    import {
        PaginationItem,
        Table,
        TableBody,
        TableBodyCell,
        TableBodyRow,
        TableHead,
        TableHeadCell
    } from "flowbite-svelte";
    import type {Item} from "../model/Item";
    export let items: Item[] = [];
    export let statement: string;
    let page: number = 0;

    const previous = () => {
        if(page > 0) {
            getPaginate()
        }
    }

    const next = () => {
        getPaginate()
    }

    const getPaginate = async () => {
        await fetch('http://localhost:8080/api/get-paginate', {
            method: 'GET',
            body: JSON.stringify({statement, page}),
            headers: {
                'Content-Type': 'application/json'
            }
        }).then(res => res.json())
            .then(value => {
                if(value.length > 0) {
                    items = value;
                }
            }).catch(() => {
                alert("error")
            });
    }
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

    <div class="flex space-x-3 m-auto mt-5">
        <PaginationItem class="flex items-center" on:click={previous}>
            <svg class="mr-2 w-5 h-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M7.707 14.707a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414l4-4a1 1 0 011.414 1.414L5.414 9H17a1 1 0 110 2H5.414l2.293 2.293a1 1 0 010 1.414z" clip-rule="evenodd"/></svg>
            Previous
        </PaginationItem>
        <PaginationItem class="flex items-center" on:click={next}>
            Next
            <svg class="ml-2 w-5 h-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg"><path fill-rule="evenodd" d="M12.293 5.293a1 1 0 011.414 0l4 4a1 1 0 010 1.414l-4 4a1 1 0 01-1.414-1.414L14.586 11H3a1 1 0 110-2h11.586l-2.293-2.293a1 1 0 010-1.414z" clip-rule="evenodd"/></svg>
        </PaginationItem>
    </div>
</div>
