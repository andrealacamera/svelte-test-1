<script>
  import {FeedbackStore} from '../stores'
  export let item

  const handleDelete = (itemId) => {
    FeedbackStore.update((currentFeedback) => {
      return currentFeedback.filter(item => item.id != itemId)
    })
  }
</script>

<div class="relative bg-white text-gray-800 border rounded-xl py-8 px-10 my-6 mx-6">
  <div class="absolute -top-3 -left-3 w-12 h-12 bg-indigo-900 text-white border rounded-full p-2 text-xl text-center">
    {item.rating}
  </div>
  <button class="absolute top-3 right-3" on:click={() => handleDelete(item.id)}>
    ✖︎
  </button>
  <p class="text-display">
    {item.text}
  </p>
</div>

