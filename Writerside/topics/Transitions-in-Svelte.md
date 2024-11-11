# Transitions in Svelte

We can make more appealing user interfaces by gracefully transitioning elements into and out of the DOM. Svelte makes 
this very easy with the transition directive.

```Typescript
<script>
	import {fade} from "svelte/transition"
	
	let visible = $state(true);
</script>

<label>
	<input type="checkbox" bind:checked={visible} />
	visible
</label>

{#if visible}
    <p transition:fade>
        Fades in and out
    </p>
{/if}
```

## Adding parameters

Transition functions can accept parameters

```Typescript
<script>
	import { fade , fly} from 'svelte/transition';

	let visible = $state(true);
</script>

<label>
	<input type="checkbox" bind:checked={visible} />
	visible
</label>

{#if visible}
	<p transition:fly={{y: 200, duration: 2000}}>
		Fades in and out
	</p>
{/if}
```

