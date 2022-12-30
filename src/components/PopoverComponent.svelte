<script lang="ts">
    import {Hr, Label, Popover, Range, Select} from "flowbite-svelte";
    import {fade} from "svelte/transition";
    import {bottom} from "@popperjs/core";
    import type {OpenAIRequest} from "../model/OpenAIRequest";

    let params: OpenAIRequest = {
        model: "code-davinci-002",
        temperature: 0,
        max_tokens: 0,
        frequency_penalty: 0,
        presence_penalty: 0,
        top_p: 0
    };

    let models = [
        {value: "code-davinci-002", name: "code-davinci-002"},
        {value: "code-cushman-001", name: "code-cushman-001"}
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
    <Range id="range-steps" min="0" max="1" bind:value={params.temperature} step="0.01"/>
    <Hr></Hr>
    <Label class="mb-1">Maximum length: {params.max_tokens}</Label>
    <Range id="range-steps" min="0" max="1" bind:value={params.max_tokens} step="0.01"/>
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