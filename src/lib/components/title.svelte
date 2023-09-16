<script lang="ts">
	const Levels: Record<number, string> = {
		1: 'text-4xl',
		2: 'text-3xl',
		3: 'text-2xl',
		4: 'text-xl',
		5: 'text-lg',
	};

	export let level: number = 1;
</script>

<svelte:element
	this={`h${level || 1}`}
	class={['mb-2 text-black/88 font-bold', Levels[level]].join(' ')}
>
	<slot />
</svelte:element>
