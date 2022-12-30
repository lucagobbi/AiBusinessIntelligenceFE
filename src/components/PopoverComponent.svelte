<script lang="ts">
    import {Hr, Label, Popover, Range, Select} from "flowbite-svelte";
    import {fade} from "svelte/transition";
    import {bottom} from "@popperjs/core";
    import type {OpenAIRequest} from "../model/OpenAIRequest";
    import {cushmanModel, daVinciModel} from "../utils/Constants";

    export let params: OpenAIRequest;

    let models = [
        {value: daVinciModel, name: daVinciModel},
        {value: cushmanModel, name: cushmanModel}
    ]

</script>

<Popover class="w-64 text-sm font-light "
         title="AI Parameters"
         triggeredBy="#send-btn"
         arrow={false}
         placement={bottom}
         transition={fade} params={{duration: 400}}
>

    <Label class="mb-1">Temperature: {params.temperature}</Label>
    <Range id="range-steps"  min="0" max="1" bind:value={params.temperature} step="0.01"/>
    <Hr></Hr>
    <Label class="mb-1">Maximum length: {params.max_tokens}</Label>
    <Range id="range-steps" min="0" max="8000" bind:value={params.max_tokens} step="1"/>
    <Hr></Hr>
    <Label class="mb-1">Frequency Penalty: {params.frequency_penalty}</Label>
    <Range id="range-steps" min="0" max="1" bind:value={params.frequency_penalty} step="0.01"/>
    <Hr></Hr>
    <Label class="mb-1">Presence Penalty: {params.presence_penalty}</Label>
    <Range id="range-steps" min="0" max="1" bind:value={params.presence_penalty} step="0.01"/>
    <Hr></Hr>
    <Label class="mb-1">Model: {params.model}</Label>
    <Select class="my-3" items={models} bind:value={params.model} />
</Popover>