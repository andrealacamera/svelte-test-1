# SVELTE-TEST-1

## Intro 
This is my first project with [Svelte](https://svelte.dev/), based on the Traversy Media Youtube video (see ref below).

Added TailwindCSS as I always do!

Several differences between video and current project are present. A few of these because Svelte changed (installation, version, etc). Other differences are due to my personal choices. Moreover I worked with SvelteKit from the beginning, so several modifications are mandatory.

## Setup the project

### Install 
Following the [docs](https://kit.svelte.dev/), the project can be installed by:
```npm
npm create svelte@latest .
``` 
(launch it inside the project folder or change `.` with `project-name`). Follows instructions during installation.

### Tailwind
Install and setup TailwindCSS following the [documentation](https://tailwindcss.com/docs/guides/sveltekit)



### Project structure
See [here](https://kit.svelte.dev/docs/project-structure) for a complete structure. I used a subset of the structure. 

Components are in the `/lib` folder, any component can be imported by: 
```js
import { MyComponent } from '$lib'
```

## Useful Notes

- In the `FeedbackForm.svelte`, the `input` element has both a `bind:value` directive and a `on:input` event handler. Surprisingly, order MATTERs! If the `on:input` is placed before the `bind:value`, the handler function gets the older value of the `text` variable and the check gives wrong results. 

- In the `RatingSelect.svelte` component, the verbose list of items has been replaced with a dynamic list created within a `#each` block. 

## Other Notes

- Removed dependencies from `uuid` package, replaced with a simple search of the max id. See [here](https://stackoverflow.com/questions/4020796/finding-the-max-value-of-an-attribute-in-an-array-of-objects) for more details.

- WRT the video, all the `<style>` elements have been replaced with Tailwind classes. I prefer this approach!

- Changed default font family with [this one](https://fonts.google.com/specimen/Exo+2).
---
## Timestamp
Created: 2023-07-06
Modified: 2023-07-10

## References:
- [TraversyMedia video](https://www.youtube.com/watch?v=3TVy6GdtNuQ)
- [TraversyMedia Github project page](https://github.com/bradtraversy/svelte-feedback-app/tree/main)
- [Svelte.dev](https://svelte.dev/)
- [SvelteKit](https://kit.svelte.dev)
- [TailwindCSS](https://tailwindcss.com/docs/guides/sveltekit)