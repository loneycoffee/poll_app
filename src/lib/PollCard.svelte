<script>
	export let poll;

	import { writable } from 'svelte/store';
	import polls from '../pollStore.js';

	let pollList = [];
	polls.subscribe((value) => {
		pollList = value;
	});

	const addVote = (option) => {
		const updatedOptions = poll.options.map((opt) => {
			if (opt === option) {
				return { ...opt, votes: opt.votes + 1 };
			} else {
				return opt;
			}
		});

		polls.update((existingPolls) => {
			return existingPolls.map((p) => {
				if (p.id === poll.id) {
					return { ...p, options: updatedOptions };
				} else {
					return p;
				}
			});
		});
	};
</script>

<div class="flex justify-center items-center">
	<div
		class="max-w-[20rem] bg-gray-700 text-white rounded-lg shadow-2xl transform transition-transform duration-300 hover:scale-105 hover:shadow-3xl relative overflow-hidden"
	>
		<div class="p-6">
			<h5 class="mb-4 text-2xl font-bold text-center leading-tight">{poll.question}</h5>
			{#each poll.options as option}
				<!-- svelte-ignore a11y-click-events-have-key-events -->
				<!-- svelte-ignore a11y-no-static-element-interactions -->
				<div
					class="bg-gray-600 text-white font-semibold rounded-lg mb-3 flex items-center justify-between px-5 py-3 shadow-lg hover:bg-gray-400 gap-4 cursor-pointer"
					on:click={() => addVote(option)}
				>
					<p>{option.text}</p>
					<p>Votes: {option.votes}</p>
				</div>
			{/each}
		</div>
		<!-- Decorative Border -->
		<div
			class="absolute inset-0 border border-gray-500 rounded-lg opacity-20 pointer-events-none"
		></div>
	</div>
</div>
