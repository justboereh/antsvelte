<script lang="ts">
	type Item = {
		href?: string;
		path?: string;
		menu?: [];
		title: '';
		onClick: (item: Item) => void | Promise<void>;
	};

	export let items: Item = [];
	export let seperator: any = '';
</script>

<div>
	{#each items as item}
		<span />
	{/each}
</div>
