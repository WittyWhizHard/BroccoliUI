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
			<svelte:fragment slot="title">{item.title}</svelte:fragment>
			<svelte:fragment slot="content">{item.content}</svelte:fragment>
		</AccordionItem>
	{/each}
</Accordion>

<Accordion collapse --accordion-width="60ch">
	{#each accordionItems as item, i}
		<AccordionItem open={i === 0}>
			<svelte:fragment slot="title">{item.title}</svelte:fragment>
			<svelte:fragment slot="content">{item.content}</svelte:fragment>
		</AccordionItem>
	{/each}
</Accordion>

<Accordion collapse --accordion-width="80ch">
    <AccordionItem>
        <svelte:fragment slot="title">title 1</svelte:fragment>
		<svelte:fragment slot="content">content 1</svelte:fragment>
    </AccordionItem>

    <AccordionItem open>
        <svelte:fragment slot="title">title 2</svelte:fragment>
        <svelte:fragment slot="content">content 2</svelte:fragment>
    </AccordionItem>
</Accordion>


TODO : animate the content open