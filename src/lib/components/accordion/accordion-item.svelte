<script>
    import {getContext} from "svelte"
    
    let { open = $bindable(false), title, content } = $props();

    const componentId = crypto.randomUUID()
    const colapse = getContext('colapse')
    const activeComponentId = getContext('active')

    function setActive(){
        $activeComponentId = componentId
    }

    function toggleOpen(){
        open = !open
    }

    function handleClick(){
        colapse ? setActive() : toggleOpen()
    }

    $effect(() => {
        open && colapse && setActive()
    });
    let isActive = $derived($activeComponentId == componentId)
    let isOpen = $derived(colapse ? isActive : open)
</script>

<div class="accordion-item">
    <button class="accordion-toggle" onclick={handleClick}>
        <div class="accordion-title">
            {@render title?.()}
        </div>
        <div
            class="caret"
            class:open={isOpen}
            class:close={!isOpen}
        >&rarr;</div>
    </button>

    {#if isOpen}
        <div class="accordion-content">
            {@render content?.()}
        </div>
    {/if}
</div>

<style>
    .accordion-toggle {
        display: flex;
        justify-content: space-between;
        align-items: center;
        width: 100%;
        padding: 1rem;
        color: inherit;
        font: inherit;
        border: none;
        background: none;
        cursor: pointer;
        border-radius: 4px;
        transition: background-color 0.1s ease;
    }

    .accordion-toggle:hover {
        background-color: hsl(220, 20%, 20%);
    }

    .accordion-content {
        padding: 1rem;
    }

    .open {
        transform: rotate(90deg);
        transition: transform 0.3s ease;
    }

    .close {
        transform: rotate(0deg);
        transition: transform 0.3s ease;
    }
</style>
