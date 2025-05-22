<script lang="ts">
	import Button from '$lib/components/button.svelte';
	import { goto } from '$app/navigation';

	function handleClick() {
		goto('/engrave');
	}
</script>

<div
	class="flex min-h-screen flex-col items-center justify-center bg-black p-10 text-center font-mono text-white"
>
	<h1 class="text-6xl font-bold">Welcome to <span class="text-yellow-500 rounded border rounded-sm px-2 py-0.5">Virtual Grave</span></h1>
	<div class="max-w-10xl flex w-full flex-col items-end">
		<h2 class="p-3 text-right text-xs italic">put your burial worries to rest!</h2>
		<Button text="engrave here" onClick={handleClick} />
	</div>
</div>
