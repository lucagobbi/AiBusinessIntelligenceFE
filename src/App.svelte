<script lang="ts">
  import {Heading, Helper, Input, Label, DarkMode} from "flowbite-svelte";
  import FooterComponent from "./components/FooterComponent.svelte";
  import SendComponent from "./components/SendComponent.svelte";
  import InfoComponent from "./components/InfoComponent.svelte";
</script>

<main class="dark:bg-slate-800 h-screen">

  <InfoComponent/>

  <Heading tag="h1" class="p-16 text-center dark:text-stone-100" customSize="text-3xl font-extrabold  md:text-4xl">
    Automated Business Intelligence
  </Heading>
  <DarkMode class="fixed right-0 top-0 mr-3 mt-4"/>

  <div class="flex flex-col justify-center items-center">
    <Label class="space-y-2 mt-3 w-9/12">
      <Input type="text" placeholder="Type here your query" size="lg" />
      <Helper class="pt-2 text-center">Write your query as if you are asking another human, not a machine.</Helper>
    </Label>
    <SendComponent/>
  </div>

  <FooterComponent/>

</main>