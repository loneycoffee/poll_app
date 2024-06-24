<script>
	import polls from '../../pollStore.js';

	let fields = { question: '', options: '' };

	const addPoll = () => {
		// Split options and initialize votes
		fields.options = fields.options.split(';').map((option) => ({ text: option.trim(), votes: 0 }));
		console.log(fields);

		// Update the polls store
		polls.update((existingPolls) => [...existingPolls, { id: Date.now(), ...fields }]);
		console.log(polls);

		// Clear fields after adding
		fields = { question: '', options: '' };
	};
</script>

<svelte:head>
	<title>Create Poll</title>
</svelte:head>

<div class="pb-10">
	<div class="pt-5 pb-10 items-center text-center">
		<h1 class="text-4xl font-extrabold no-underline text-gray-700">Create a poll</h1>
	</div>
	<form on:submit|preventDefault={addPoll} class="flex flex-col items-center space-y-4">
		<div class="flex flex-col items-center justify-center space-y-2 w-full">
			<label for="question" class="text-2xl font-semibold no-underline text-gray-700"
				>Question</label
			>
			<input
				type="text"
				id="question"
				class="border-2 border-gray-500 rounded-lg p-2 w-1/2"
				placeholder="e.g., What is the best color?"
				bind:value={fields.question}
			/>
		</div>
		<button class="flex flex-col items-center justify-center space-y-2 w-full">
			<label for="options" class="text-2xl font-semibold no-underline text-gray-700">Options</label>
			<input
				type="text"
				id="options"
				class="border-2 border-gray-500 rounded-lg p-2 w-1/2"
				placeholder="e.g., Red;Blue;Green"
				bind:value={fields.options}
			/>
		</button>
		<div class="flex justify-center w-full">
			<button
				class="w-1/2 bg-gray-500 hover:bg-gray-400 text-white font-bold py-2 px-4 border-b-4 border-gray-600 hover:border-gray-500 rounded flex justify-center items-center"
			>
				<svg
					class="mr-2 text-gray-800 dark:text-white"
					aria-hidden="true"
					xmlns="http://www.w3.org/2000/svg"
					width="24"
					height="24"
					fill="none"
					viewBox="0 0 24 24"
				>
					<path
						stroke="currentColor"
						stroke-linecap="round"
						stroke-linejoin="round"
						stroke-width="2"
						d="M12 7.757v8.486M7.757 12h8.486M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z"
					/>
				</svg>
				Create Poll
			</button>
		</div>
	</form>
</div>
