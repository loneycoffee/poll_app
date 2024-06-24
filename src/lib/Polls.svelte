<script>
	import polls from '../pollStore.js';
	import PollCard from './PollCard.svelte';
	let pollList = [];

	// Subscribe to the poll store to get the latest polls
	polls.subscribe((value) => {
		pollList = value;
		console.log(pollList);
	});
</script>

<div class="justify-center flex flex-wrap pb-10 gap-6">
	{#each pollList as poll (poll.id)}
		<PollCard class="bg-red-500" {poll} />
	{/each}
</div>
