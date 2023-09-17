<script>
	import { onMount } from 'svelte';

	/**
	 * @type {HTMLDivElement}
	 */
	let nodeRef;
	let isMounted = false;
	export let danger = false;
	export let round = false;

	onMount(() => {
		setTimeout(() => (isMounted = true), 10);

		setTimeout(() => {
			nodeRef.parentNode?.removeChild(nodeRef);
		}, 500);
	});

	$: classes = [
		'absolute w-full h-full box-content top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 transition-all duration-500 pointer-events-none',
		isMounted
			? 'border-white/0 border-8'
			: (danger ? 'border-red-5/50' : 'border-blue-5/50') + ' border-2',
		round ? 'rounded-full' : isMounted ? 'rounded-xl' : 'rounded-lg',
	];
</script>

<div bind:this={nodeRef} class={classes.join(' ')} />
