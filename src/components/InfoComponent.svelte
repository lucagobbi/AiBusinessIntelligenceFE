<script>
    import {Modal} from "flowbite-svelte";
    let defaultModal = false;
</script>




<div class="fixed left-0 top-0 mt-6 ml-5">
    <svg class="hover:scale-105" on:click={() => defaultModal = true} fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8.228 9c.549-1.165 2.03-2 3.772-2 2.21 0 4 1.343 4 3 0 1.4-1.278 2.575-3.006 2.907-.542.104-.994.54-.994 1.093m0 3h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
</div>

<Modal title="About Automated BI" bind:open={defaultModal} autoclose>
    <p class="text-base leading-relaxed text-gray-500 dark:text-gray-400">
        Automated BI is a user-friendly application that helps you extract and analyze data from your database using natural language queries. Instead of writing complex code or SQL statements, you can simply type out your request in plain English and Automated BI will use the power of OpenAI's APIs to understand and execute your request. With Automated BI, you can easily access the insights and information you need to make informed business decisions, all from the convenience of a single, intuitive platform.
    </p>
</Modal>

<style>
    svg {
        width: 22px;
        height: 22px;
        cursor: pointer;
    }
</style>