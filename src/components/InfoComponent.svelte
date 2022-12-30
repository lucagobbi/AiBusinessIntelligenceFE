<script xmlns="http://www.w3.org/1999/html">
    import {Accordion, AccordionItem, Heading, Li, List, Modal} from "flowbite-svelte";
    let defaultModal = false;
</script>




<div class="fixed left-0 top-0 mt-6 ml-5">
    <svg class="hover:scale-110 text-stone-300" on:click={() => defaultModal = true} fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M8.228 9c.549-1.165 2.03-2 3.772-2 2.21 0 4 1.343 4 3 0 1.4-1.278 2.575-3.006 2.907-.542.104-.994.54-.994 1.093m0 3h.01M21 12a9 9 0 11-18 0 9 9 0 0118 0z"></path></svg>
</div>

<Modal title="About Automated BI" class="p-1" bind:open={defaultModal} size="lg">

    <p class="text-base leading-relaxed text-gray-500 dark:text-gray-400">
        Automated BI is a user-friendly application that helps you extract and analyze data from your database using natural language queries. Instead of writing complex code or SQL statements, you can simply type out your request in plain English and Automated BI will use the power of OpenAI's APIs to understand and execute your request. With Automated BI, you can easily access the insights and information you need to make informed business decisions, all from the convenience of a single, intuitive platform.
    </p>

    <Heading tag="h3" customSize="text-xl">FAQ</Heading>
    <Accordion>
        <AccordionItem>
            <span slot="header">Can I customize the AI algorithms used by Automated BI to fit my specific needs?</span>
            <p class="mb-2 text-gray-500 dark:text-gray-400">
                Yes, you can customize the AI algorithms used by Automated BI to fit your specific needs. When you make a query, you have the option to set various parameters that can adjust the behavior of the AI algorithms. For example, you can specify the level of precision or accuracy you desire, or you can set constraints on the type of data that should be returned. By adjusting these parameters, you can tailor the AI algorithms to fit your unique business requirements and ensure that you are getting the most relevant and accurate results.
            </p>
        </AccordionItem>
        <AccordionItem>
            <span slot="header">What are the parameters that I can modify in Automated BI?</span>
            <p class="mb-2 text-gray-500 dark:text-gray-400">
                There are several parameters that you can modify in Automated BI to customize the AI algorithms to fit your specific needs. These include:
            <p>
            <List tag="ul" ulClass="max-w-max">
                <Li class="mb-2">
                    <span class="font-bold">Temperature</span>: this parameter controls the randomness of the AI algorithm, with a lower temperature resulting in a more deterministic output.
                </Li>
                <Li class="mb-2">
                    <span class="font-bold">Maximum length</span>: this parameter determines the maximum number of tokens (units of meaning in a language) that the AI algorithm will consider when generating a response.
                </Li>
                <Li class="mb-2">
                    <span class="font-bold">Frequency penalty</span>: this parameter can be used to reduce the repetition of answers and encourage the AI algorithm to generate more varied responses.
                </Li>
                <Li class="mb-2">
                    <span class="font-bold">Presence penalty</span>: this parameter can be used to increase the probability of new topics and answers, encouraging the AI algorithm to explore novel areas of discussion.
                </Li>
            </List>
            <p class="mb-2 text-gray-500 dark:text-gray-400">
                By adjusting these parameters, you can fine-tune the behavior of the AI algorithms to fit your specific needs and ensure that you are getting the most relevant and accurate results.
            </p>
        </AccordionItem>
        <AccordionItem>
            <span slot="header">Can I select a different AI model in Automated BI?</span>
            <p class="mb-2 text-gray-500 dark:text-gray-400">
                Yes, it is possible to choose between different AI models in Automated BI. Currently, there are two models available: "code-davinci-002" and "code-cushman-001".
            </p>
            <List tag="ul" ulClass="max-w-max">
                <Li class="mb-2">
                    The <span class="font-bold">"code-davinci-002"</span> model is the most capable model in the Codex series, and is able to understand and generate code. It is highly accurate and can handle a wide range of tasks and requests.
                </Li>
                <Li class="mb-2">
                    The <span class="font-bold">"code-cushman-001"</span> model is also highly capable, with performance similar to the "code-davinci-002" model. However, it is slightly faster and may be a good choice if you need to process large volumes of data or queries in a short amount of time.
                </Li>
            </List>
            <p class="mb-2 text-gray-500 dark:text-gray-400">
                You can choose the AI model that best fits your needs and requirements by selecting it in the settings or configuration menu of Automated BI.
            </p>
        </AccordionItem>
    </Accordion>
</Modal>

<style>
    svg {
        width: 22px;
        height: 22px;
        cursor: pointer;
    }
</style>