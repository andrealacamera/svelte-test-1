<script>
  import { fade, scale } from 'svelte/transition'
  import {FeedbackStore} from '../stores'
  import FeedbackItem from '$lib/FeedbackItem.svelte'
</script>

{#each $FeedbackStore as item (item.id)}
<div in:scale out:fade={{ duration: 200 }}>
  <FeedbackItem {item} />
</div>
{/each}