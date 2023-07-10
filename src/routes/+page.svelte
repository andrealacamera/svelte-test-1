<script>
	import FeedbackForm from '$lib/FeedbackForm.svelte'
	import FeedbackList from '$lib/FeedbackList.svelte'
	import FeedbackStats from '$lib/FeedbackStats.svelte'
</script>

<main class="max-w-[1024px] m-auto bg-gray-200 py-8 px-4">
	<FeedbackForm />
	<FeedbackStats />
	<FeedbackList />
</main>