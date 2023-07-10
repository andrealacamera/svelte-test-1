<script>
  import {FeedbackStore} from '../stores'

  $: count = $FeedbackStore.length
  $: average = $FeedbackStore.reduce((a, {rating}) => a + rating, 0) / $FeedbackStore.length
</script>

{#if count>0}
<div class="flex justify-between items-center m-4 text-indigo-900 font-bold">
  <h4>{count} Reviews</h4>
  <h4>Ratings Average: {average.toFixed(2)}</h4>
</div>
{/if}