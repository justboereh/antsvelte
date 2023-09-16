<script lang="ts">
	type Shape = 'default' | 'circle' | 'round';
	type Size = 'default' | 'small' | 'large';
	type Type = 'default' | 'primary' | 'dashed' | 'link' | 'text';

	export let block: boolean = false;
	export let danger: boolean = false;
	export let disabled: boolean = false;
	export let ghost: boolean = false;
	export let href: string = '';
	export let htmlType: string = '';
	export let loading: boolean = false;
	export let shape: Shape = 'default';
	export let size: Size = 'default';
	export let target: string = '';
	export let type: Type = 'default';

	const Sizes: Record<Size, string> = {
		default: 'text-base px-4 h-8',
		small: 'text-base px-2 h-6',
		large: 'text-md px-4 h-10',
	};

	const Types: Record<Type, string> = {
		default:
			'bg-white border-gray-5 hover:text-blue-7 hover:border-blue-7 active:text-blue-5 active:border-blue-5',
		primary: 'bg-blue-6 hover:bg-blue-7 active:bg-blue-5 text-white border-0',
		dashed:
			'bg-white border-gray-5 border-dashed hover:text-blue-7 hover:border-blue-7 active:text-blue-5 active:border-blue-5',
		link: 'border-0 text-blue-6 hover:text-blue-7 active:text-blue-5',
		text: 'border-0 hover:bg-gray-4 active:bg-gray-5',
	};

	$: classes = [
		'border rounded-md transition duration-200',
		Sizes[size] || Sizes.default,
		Types[type] || Types.default,
	];
</script>

<svelte:element this={!href ? 'button' : 'a'} class={classes.join(' ')}>
	<slot name="icon" />

	<slot />
</svelte:element>
