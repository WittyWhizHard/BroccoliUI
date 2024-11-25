<script>
    import { setContext } from "svelte";
    import { writable } from "svelte/store";

    export let colapse = false

    const activeComponentId = writable(null)

    setContext('colapse', colapse)
    setContext('active', activeComponentId)
</script>


<div class="accordion">
    <slot />
</div>

<style>
    .accordion{
        width: 60ch;
        padding: 1rem;
        color: hsl(220,10%,100%);
        background-color: hsl(220,10%,10%);
        border-radius: 4px;
        box-shadow: 0px 1px 20px hsl(220,10%,8%);
    }
</style>