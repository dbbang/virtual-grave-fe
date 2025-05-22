<script lang="ts">
	import Button from '$lib/components/button.svelte';
	import Input from '$lib/components/input.svelte';

	let name = $state('');
	let birthDate = $state('');
	let deathDate = $state('');
	let obituary = $state('');
	let epitaph = $state('');
	let enableComments = $state(false);

	const handleEnableComments = (event: Event & { currentTarget: HTMLInputElement }) => {
		const input = event.currentTarget.checked;
		enableComments = input;
	};

	const handleSave = async () => {
		const attributes = {
			name,
			birthDate,
			deathDate,
			obituary,
			epitaph,
			enableComments
		};

		try {
			const response = await fetch('http://localhost:3306/', {
				method: 'POST',
				headers: {
					'Content-Type': 'application/json'
				},
				body: JSON.stringify(attributes)
			});
			if (!response.ok) {
				throw new Error('Failed to save memorial');
			}
			// Optionally handle success (e.g., redirect or show a message)
			console.log('Memorial saved!');
		} catch (error) {
			console.error(error);
		}
	};
</script>

<div class="mx-auto flex w-full max-w-md flex-col gap-4 p-4">
	<h1 class="border-red mb-2 rounded bg-red-500 p-1">Create memorial.</h1>
	<Input text="Name" bind:value={name} />
	<Input text="Birth Date" type="date" bind:value={birthDate} />
	<Input text="Death Date" type="date" bind:value={deathDate} />
	<Input text="Obituary" bind:value={obituary} />
	<Input text="Epitaph" bind:value={epitaph} />
	<label class="items-left flex w-full gap-2">
		Enable comments
		<input
			class="flex-1 rounded border border-white"
			type="checkbox"
			onchange={handleEnableComments}
			value={enableComments}
		/>
	</label>
</div>

<div>
	<Button text="Save." on:click={handleSave}></Button>
</div>
