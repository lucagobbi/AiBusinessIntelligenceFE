<script>
    import {Button, Spinner} from "flowbite-svelte";
    import PopoverComponent from "./PopoverComponent.svelte";

    let loading = false;

    const send = () => {
        loading = !loading;
    }
</script>

<Button gradient color="blue" id="send-btn" class="mt-4 outline-none border-none focus:outline-none w-1/5" on:click={send}>
    {#if loading}
        <Spinner class="mr-3" size="4" color="white" />Loading ...
    {:else }
        Send
    {/if}
</Button>

<PopoverComponent/>

