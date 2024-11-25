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
            {#snippet title()}
                {item.title}
            {/snippet}
            {#snippet content()}
                {item.content}
            {/snippet}
        </AccordionItem>
    {/each}
</Accordion>

<Accordion colapse>
    <AccordionItem>
        {#snippet title()}
            title 1
        {/snippet}
        {#snippet content()}
            content 1
        {/snippet}
    </AccordionItem>

    <AccordionItem>
        {#snippet title()}
            title 2
        {/snippet}
        {#snippet content()}
            content 2
        {/snippet}
    </AccordionItem>
</Accordion>


TODO : animate the content open