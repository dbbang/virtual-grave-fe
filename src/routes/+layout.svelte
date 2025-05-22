<script lang="ts">
	import '../app.css';

	let { children } = $props();
</script>

<div
	class="flex min-h-screen flex-col items-center justify-center bg-black text-center font-mono text-white"
>
	{@render children()}
</div>
