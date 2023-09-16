<script lang="ts">
	type Type = 'default' | 'secondary' | 'success' | 'warning' | 'danger';

	const Types: Record<Type, string> = {
		default: '',
		secondary: 'text-gray-7',
		success: 'text-success',
		warning: 'text-warning',
		danger: 'text-error',
	};

	const ElementClasses: Record<string, string> = {
		mark: 'bg-gold-9',
		code: 'border border-gray-8/20 rounded px-1.5 py-0.5 text-sm bg-gray-7/10',
		kbd: 'border border-b-2 border-gray-8/20 rounded px-1.5 py-0.5 text-sm bg-gray-7/10',
		del: '',
		u: '',
		strong: '',
		i: '',
	};

	export let type: Type = 'default';
	export let mark: boolean = false;
	export let code: boolean = false;
	export let keyboard: boolean = false;
	export let underline: boolean = false;
	let deleteP: boolean = false;
	export let strong: boolean = false;
	export let italic: boolean = false;
	export let copyable: boolean = false; // TODO
	export let disabled: boolean = false; // TODO
	export let editable: boolean = false; // TODO
	export let ellipsis: boolean = false; // TODO

	let element = '';

	const SetElement = () => {
		if (mark) return 'mark';
		if (code) return 'code';
		if (keyboard) return 'kbd';
		if (deleteP) return 'del';
		if (underline) return 'u';
		if (strong) return 'strong';
		if (italic) return 'i';

		return '';
	};

	$: element = SetElement();
	$: elClasses = ElementClasses[element];
	$: classes = [
		'text-gray-12',
		Types[type] || Types.default,
		disabled ? 'cursor-not-allowed select-none text-gray-5' : '',
	];

	export { deleteP as delete };
</script>

<span class={classes.join(' ')}>
	<svelte:element this={element} class={elClasses}>
		<slot />
	</svelte:element>

	{#if !element}
		<slot />
	{/if}
</span>
