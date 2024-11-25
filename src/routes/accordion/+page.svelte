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

<Accordion collapse --accordion-width="40ch">
    {#each accordionItems as item}
        <AccordionItem>
            {#snippet title()}
                {item.title}
            {/snippet}
            {#snippet content()}
                {item.content}
            {/snippet}
        </AccordionItem>
    {/each}
</Accordion>

<Accordion collapse --accordion-width="60ch">
    {#each accordionItems as item, i}
        <AccordionItem open={i === 0}>
            {#snippet title()}
                {item.title}
            {/snippet}
            {#snippet content()}
                {item.content}
            {/snippet}
        </AccordionItem>
    {/each}
</Accordion>

<Accordion collapse --accordion-width="80ch">
    <AccordionItem>
        {#snippet title()}
            title 1
        {/snippet}
        {#snippet content()}
            content 1
        {/snippet}
    </AccordionItem>

    <AccordionItem open>
        {#snippet title()}
            title 2
        {/snippet}
        {#snippet content()}
            content 2
        {/snippet}
    </AccordionItem>
</Accordion>
