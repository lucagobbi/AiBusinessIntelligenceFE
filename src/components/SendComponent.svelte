<script lang="ts">
    import {Button, Spinner, Toast} from "flowbite-svelte";
    import PopoverComponent from "./PopoverComponent.svelte";
    import type {OpenAIRequest} from "../model/OpenAIRequest";
    import {createEventDispatcher} from "svelte";
    import {fade} from "svelte/transition";

    const dispatch = createEventDispatcher();

    let loading: boolean = false;
    let error: boolean = false;
    export let openAiRequest: OpenAIRequest;

    const send = async () => {
        loading = true;
        await fetch('http://localhost:8080/api/query-raw', {
            method: 'POST',
            body: JSON.stringify(openAiRequest),
            headers: {
                'Content-Type': 'application/json'
            }
        }).then(res => res.json())
        .then(value => {
            sqlEvent(value.sqlStatement);
            if(value.resultSet.length === 0) {
                error = true;
            }
            resultEvent(value.resultSet);
        }).catch(() => {
            error = true;
        }).finally(() => {
            loading = false;
        });
    }

    const sqlEvent = (sqlStatement: string) => {
        dispatch('sql', {
            text: sqlStatement
        });
    }

    const resultEvent = (resultSet) => {
        dispatch('result', {
            detail: resultSet
        })
    }

</script>
<Button gradient color="blue" id="send-btn" class="mt-4 outline-none border-none focus:outline-none w-1/5 lg:w-1/6" on:click={send}>
    {#if loading}
        <Spinner class="mr-3" size="4" color="white" />Loading ...
    {:else }
        Send
    {/if}
</Button>

<PopoverComponent bind:params={openAiRequest}/>

<Toast class="bg-red-500" transition={fade} bind:open={error} on:close={()=>{error=false}}>
    Something went wrong!
</Toast>