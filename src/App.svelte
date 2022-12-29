<script lang="ts">
  import {Button, Heading, Helper, Input, Label, Spinner} from "flowbite-svelte";

  let loading: boolean = false;

  const send = () => {
    loading = !loading;
  }

</script>

<main class="h-screen">
  <Heading tag="h2" class="text-stone-300" customSize="text-4xl font-extrabold  md:text-5xl lg:text-6xl">
    Automated Business Intelligence
  </Heading>

  <Label class="space-y-2 mt-16">
    <Input type="text" placeholder="Type here your query" size="lg" />
    <Helper class="pt-2">Write your query as if you are asking another human, not a machine.</Helper>
  </Label>
  <Button gradient color="blue" class="mt-4 outline-none border-none focus:outline-none" on:click={send}>
    {#if loading}
    <Spinner class="mr-3" size="4" color="white" />Loading ...
      {:else }
      Send
      {/if}
  </Button>

</main>