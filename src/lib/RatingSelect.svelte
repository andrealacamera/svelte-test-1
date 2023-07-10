<script>
  let selections = [1,2,3,4,5,6,7,8,9,10]
  export let selected = null // bind the value

  const handleChange = (e) => {
    selected = e.currentTarget.value
  }
</script>

<ul class="flex flex-row justify-around my-8">
  {#each selections as sel, i} 
    <li> 
      <input class="hidden peer" type="radio" id={sel} name="rating" value={sel} on:change={handleChange} checked={sel==selected}/>
      <label class="inline-flex items-center justify-center w-12 h-12 p-2 rounded-full  {sel==selected ? 'bg-indigo-900 text-indigo-100' : 'bg-indigo-100 text-indigo-900'}" for={sel}>{sel}</label>
    </li>
  {/each}
</ul>