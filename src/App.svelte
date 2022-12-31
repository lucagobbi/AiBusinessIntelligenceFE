<script lang="ts">
  import {Heading, Helper, Input, Label, DarkMode} from "flowbite-svelte";
  import FooterComponent from "./components/FooterComponent.svelte";
  import SendComponent from "./components/SendComponent.svelte";
  import InfoComponent from "./components/InfoComponent.svelte";
  import ResultComponent from "./components/ResultComponent.svelte";
  import type {Item} from "./model/Item";
  import type {OpenAIRequest} from "./model/OpenAIRequest";
  import {daVinciModel} from "./utils/Constants";

  let extraction: boolean = false;
  let query: string = "Give me all the items with a price lower than two hundred dollars";
  let statement: string;
  let result: Item[];

  export let openAiRequest: OpenAIRequest= {
    model: daVinciModel,
    prompt: query,
    temperature: 0,
    max_tokens: 150,
    frequency_penalty: 0,
    presence_penalty: 0
  };

  const setStatement = (event) => {
    statement = event.detail.text;
  }

  const setResult = (event) => {
    extraction = true;
    result = event.detail.detail;
  }

  const setPrompt = () => {
    openAiRequest.prompt = query;
  }

</script>

<main class="dark:bg-slate-800 h-screen">

  <InfoComponent/>

  <Heading tag="h1" class="p-16 text-center dark:text-stone-100" customSize="text-3xl font-extrabold  md:text-4xl">
    Automated Business Intelligence
  </Heading>
  <DarkMode class="fixed right-0 top-0 mr-3 mt-4"/>

  <div class="flex flex-col justify-center items-center">
    <Label class="space-y-2 mt-3 w-9/12 lg:w-7/12">
      <Input type="text" placeholder="Type here your query" size="lg" bind:value={query} on:input={setPrompt}/>
      <Helper class="pt-2 text-center">Write your query as if you are asking another human, not a machine.</Helper>
    </Label>
    <SendComponent bind:openAiRequest={openAiRequest} on:sql={setStatement} on:result={setResult}/>
  </div>

  {#if extraction}
    <h6 class="mt-5 mb-2 text-stone-300 text-center">{statement}</h6>
  <div class="w-full flex justify-center">
    <ResultComponent {statement} items={result}/>
  </div>
  {/if}

  <FooterComponent/>
</main>