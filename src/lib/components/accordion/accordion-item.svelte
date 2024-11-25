<script>
    import { slide } from "svelte/transition";

    let { open = $bindable(false), title, content } = $props();
    const componentId = crypto.randomUUID()

    function toggleOpen() {
        open = !open;
    }
</script>

<div class="accordion-item">
    <button
        onclick={toggleOpen}
        class="accordion-toggle"
        aria-expanded={open}
        aria-controls="accordion-{componentId}"
    >
        <div class="accordion-title">
            {@render title?.()}
        </div>

        <div class="accordion-caret" class:open={open}>👉️</div>
    </button>

    {#if open}
        <div
            transition:slide|local
            class="accordion-content"
            role="region"
            aria-hidden={!open}
            aria-labelledby="accordion-{componentId}"
        >
            {@render content?.()}
        </div>
    {/if}
</div>

<style>
    .accordion-toggle {
        width: 100%;
        display: flex;
        justify-content: space-between;
        padding: var(--accordion-padding, 1rem);
        color: var(--accordion-color, inherit);
        font: inherit;
        font-weight: 600;
        border: none;
        background: none;
        cursor: pointer;
        border-radius: var(--accordion-radius, 4px);
        transition: background-color 0.1s ease;
    }

    .accordion-toggle:hover {
        background-color: var(--accordion-hover, hsl(220 20% 20%));
    }

    .accordion-content {
        padding: var(--accordion-content-padding, 1rem);
    }

    .accordion-caret {
        transition: rotate 0.3s ease;
    }

    .open {
        rotate: 90deg;
    }
</style>
