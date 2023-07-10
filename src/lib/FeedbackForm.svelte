<script>
    import {FeedbackStore} from '../stores'
    import RatingSelect from './RatingSelect.svelte'
    
    let text = ''
    let rating = null
    let btnDisabled = true
    let min = 5
    let message

    // const handleSelect = e => rating = e.detail
    const handleInput = (e) => {
      if (text.trim().length < min) {
        message = `Text must be at least ${min} characters`
        btnDisabled = true
      } else {
        message = null
        btnDisabled = false
      }
    }

    const handleSubmit = () => {
      if (!rating) {
        message = 'Please enter a rate before submitting your comment..'
      } else if (text.trim().length >= min )  {
        let maxItem = $FeedbackStore.reduce((prev,curr) => prev.id>curr.id ? prev : curr, {id:0})
        const newFeedback = {
          id: maxItem.id+1,
          text,
          rating: +rating
        }

        FeedbackStore.update((currentFeedback) => {
          return [newFeedback, ...currentFeedback]
        })
        text = ''
        rating=null
        message = null
      }
    }
</script>

<header>
  <h2 class="text-2xl text-center font-bold">How would you rate your service with us?</h2>
</header>
<form on:submit|preventDefault={handleSubmit}>
  <RatingSelect bind:selected={rating} />
  <div class="flex flex-row border rounded p-2 mt-4">
    <input class="flex-grow rounded-lg px-2" type="text" bind:value={text}  on:input={handleInput} placeholder="Tell us something that keeps you coming back">
    <button class="bg-indigo-900 text-indigo-50 px-4 py-2 rounded-lg {btnDisabled ? 'opacity-50 cursor-not-allowed' : ''}" disabled={btnDisabled} type="submit">Send</button>
  </div>
  {#if message}
    <div class="text-red-500 text-sm italic">
      {message}
    </div>
  {/if}
</form>