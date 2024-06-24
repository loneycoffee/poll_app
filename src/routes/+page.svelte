<script>
	import Polls from '$lib/Polls.svelte';
</script>

<svelte:head>
	<title>Home</title>
</svelte:head>

<div class="container mx-auto px-4">
	<div class="flex justify-center pt-8 pb-12">
		<h1 class="text-5xl text-center font-extrabold tracking-tight text-gray-800 leading-snug">
			Create polls easily!
		</h1>
	</div>

	<div class="grid grid-cols-1 sm:grid-cols-2 gap-8 px-4">
		<div
			class="flex flex-col items-center text-center p-6 bg-white rounded-lg shadow-md transition-transform transform hover:scale-105"
		>
			<h2 class="text-3xl font-semibold text-gray-800 mb-4">Create a poll</h2>
			<p class="text-xl text-gray-600">
				Create a poll in a few seconds and share it with your friends.
			</p>
		</div>
		<div
			class="flex flex-col items-center text-center p-6 bg-white rounded-lg shadow-md transition-transform transform hover:scale-105"
		>
			<h2 class="text-3xl font-semibold text-gray-800 mb-4">Vote</h2>
			<p class="text-xl text-gray-600">Vote in the polls you have access to.</p>
		</div>
	</div>

	<div class="pt-12 pb-12">
		<h1 class="text-4xl font-extrabold text-center text-gray-800 mb-8">Check the latest polls:</h1>
		<div class="px-4">
			<Polls />
		</div>
	</div>
</div>

<style>
	:global(body) {
		background-color: #f7fafc; /* Light gray background */
	}
</style>
