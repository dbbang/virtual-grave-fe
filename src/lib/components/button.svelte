<script lang="ts">
	export let text: string = '';
	export let disabled: boolean = false;
	export let onClick: (() => void) | undefined = undefined;

	const handleClick = () => {
		onClick?.();
	};
</script>

<button
	class="rounded bg-red-500 p-1 text-xs text-white disabled:opacity-50 cursor-pointer"
	{disabled}
	on:click={handleClick}
>
	{text}
</button>
