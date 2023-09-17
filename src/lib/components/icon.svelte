<script lang="ts">
	type Type = 'outlined' | 'filled' | 'twotone';
	export let type: Type = 'outlined';
	export let name: string = undefined;

	$: icon = await import(`./icons/${type}/${name}`);
</script>

<svelte:component this={icon} class="text-base" />
