<script>
    import { Accordion, AccordionItem } from "$lib";

    const accordionItems = [
        { title: "title 1", content: "content 1" },
        { title: "title 2", content: "content 2" },
        { title: "title 3", content: "content 3" },
        { title: "title 4", content: "content 4" },
    ];
</script>

<a href="./">back</a>

<Accordion colapse>
    {#each accordionItems as item}
        <AccordionItem>
            <svelte:fragment slot="title">{item.title}</svelte:fragment>
            <svelte:fragment slot="content">{item.content}</svelte:fragment>
        </AccordionItem>
    {/each}
</Accordion>

<Accordion colapse>
    <AccordionItem>
        <svelte:fragment slot="title">title 1</svelte:fragment>
        <svelte:fragment slot="content">content 1</svelte:fragment>
    </AccordionItem>

    <AccordionItem>
        <svelte:fragment slot="title">title 2</svelte:fragment>
        <svelte:fragment slot="content">content 2</svelte:fragment>
    </AccordionItem>
</Accordion>
