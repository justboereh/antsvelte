<script lang="ts">
	import Loading from './icons/outlined/loading.svelte';
	import Wave from '../utils/wave.svelte';

	type Shape = 'default' | 'circle' | 'round';
	type Size = 'default' | 'small' | 'large';
	type Type = 'default' | 'primary' | 'dashed' | 'link' | 'text';
	type HTMLType = 'button' | 'submit' | 'reset' | null | undefined;

	export let block: boolean = false;
	export let danger: boolean = false;
	export let disabled: boolean = false;
	export let ghost: boolean = false;
	export let href: string = '';
	export let htmlType: HTMLType = null;
	export let loading: boolean = false;
	export let shape: Shape = 'default';
	export let size: Size = 'default';
	export let target: string = '';
	export let type: Type = 'default';

	const Sizes: Record<Size, string> = {
		default: ['text-base h-8', shape === 'circle' ? 'w-8' : 'px-4'].join(' '),
		small: ['text-base h-6', shape === 'circle' ? 'w-6' : 'px-2'].join(' '),
		large: ['text-md h-10', shape === 'circle' ? 'w-10' : 'px-4'].join(' '),
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

	const DangerTypes: Record<Type, string> = {
		default:
			'bg-white text-red-6 border-red-6 hover:text-red-7 hover:border-red-7 active:text-red-5 active:border-red-5',
		primary: 'text-white bg-red-6 hover:bg-red-7 active:bg-red-5 border-0',
		dashed:
			'bg-white text-red-6 border-red-5 border-dashed hover:text-red-7 hover:border-red-7 active:text-red-5 active:border-red-5',
		link: 'border-0 text-red-6 hover:text-red-7 active:text-red-5',
		text: 'border-0 text-red-6 hover:bg-red-10/40',
	};

	const DisabledTypes: Record<Type, string> = {
		default: 'bg-gray-3 text-gray-6 border-gray-5 cursor-not-allowed',
		primary: 'bg-gray-3 text-gray-5 border-gray-5 cursor-not-allowed',
		dashed: 'bg-gray-3 text-gray-6 border-gray-5 border-dashed cursor-not-allowed',
		link: 'border-0 text-gray-6 cursor-not-allowed',
		text: 'border-0 text-gray-6 cursor-not-allowed',
	};

	let waves = 0;

	$: classes = GetClasses();

	function GetClasses() {
		const classes = ['border transition duration-200 relative flex items-center gap-2'];
		const isToCircle = ['circle', 'round'].includes(shape);

		classes.push(Sizes[size] || Sizes.default);
		classes.push(isToCircle ? 'rounded-full justify-center' : 'rounded-md');

		if (disabled) {
			classes.push(DisabledTypes[type] || DisabledTypes.default);

			return classes;
		}

		if (danger) {
			classes.push(DangerTypes[type] || DangerTypes.default);

			return classes;
		}

		classes.push(Types[type] || Types.default);

		return classes;
	}

	function NewWave() {
		if (disabled) return;
		if (['text', 'link'].includes(type)) return;

		waves++;
	}
</script>

<button class={classes.join(' ')} on:click={NewWave} type={htmlType}>
	{#if !loading}
		<slot name="icon" />
	{/if}

	{#if loading}
		<Loading />
	{/if}

	<slot />

	{#each [...Array(waves)] as _}
		<Wave {danger} round={['circle', 'round'].includes(shape)} />
	{/each}
</button>
