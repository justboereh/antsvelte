<script lang="ts">
    export let level: number = 1
</script>


<svelte:element this={`h${level || 1}`} class="ant-typography">
    <slot />
</svelte:element>