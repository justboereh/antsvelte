<script lang="ts">
    type Size = 'default' | 'tiny' | 'small' | 'medium' | 'large' | 'larger' | 'massive'
    type Type = 'default' | 'secondary' | 'success' | 'warning' | 'danger'

	export let size: Size = 'default';
	export let type: Type = 'default';
	export let mark: boolean = false;
	export let code: boolean = false;
	export let keyboard: boolean = false;
	export let underline: boolean = false;
	let deleteP: boolean = false;
	export let strong: boolean = false;
	export let italic: boolean = false;
	export let copyable: boolean = false;
	export let disabled: boolean = false;
	export let editable: boolean = false;
	export let ellipsis: boolean = false;

	let element = ''

	const SetElement = () => {
		if (mark) return  'mark'
		if (code) return  'code'
		if (keyboard) return  'kbd'
		if (deleteP) return  'del'
		if (underline) return  'u'
		if (strong) return  'strong'
		if (italic) return  'i'
		
		return ''
	}

	$: element = SetElement()

    export {deleteP as delete}
</script>	

<span class="ant-typography ant-typography-{disabled ? 'disabled' : type}">
	<svelte:element this={element}>
		<slot />
	</svelte:element>

	{#if !element}
		<slot />
	{/if}
</span>
