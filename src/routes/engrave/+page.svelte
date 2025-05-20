<script lang="ts">
	let name = $state('');
	let deathDate = $state();
	let enableComments = $state(false);

	const handleNameChange = (event: Event & { currentTarget: HTMLInputElement }) => {
		const input = event.currentTarget.value;
		name = input;
	};

	const handleDeathDateChange = (event: Event & { currentTarget: HTMLInputElement }) => {
		const input = event.currentTarget.value;
		const dateObj = new Date(input);

		const unixEpoch = dateObj.valueOf();
		deathDate = unixEpoch;
	};

	const handleEnableComments = (event: Event & { currentTarget: HTMLInputElement }) => {
		console.log(event)
		const input = event.currentTarget.checked;
		enableComments = input;
	};
</script>

<div class="flex w-full flex-col items-center gap-4 p-4">
	<h1 class="text-xl font-bold">Create memorial</h1>
	<label>
		Name
		<input class="rounded-md border px-2 py-1" onchange={handleNameChange} value={name} />
	</label>
	<label>
		Death Date
		<input
			class="rounded-md border px-2 py-1"
			type="date"
			onchange={handleDeathDateChange}
			value={deathDate}
		/>
	</label>
	<label>
		Enable comments
		<input
			class="rounded-md border px-2 py-1"
			type="checkbox"
			onchange={handleEnableComments}
			value={enableComments}
		/>
	</label>
</div>
