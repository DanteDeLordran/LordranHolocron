# Errors and Redirects in SvelteKit

There are two types of errors in SvelteKit — expected errors and unexpected errors.

## Expected

An expected error is one that was thrown via the error helper from @sveltejs/kit, as in 
src/routes/expected/+page.server.js

```TypeScript
import { error } from '@sveltejs/kit';

export function load() {
	error(420, 'Enhance your calm');
}
```

## Unexpected

```TypeScript
export function load() {
	throw new Error('Kaboom!');
}
```

## Error pages

When something goes wrong inside a load function, SvelteKit renders an error page.

The default error page is somewhat bland. We can customize it by creating a src/routes/+error.svelte component

```
<script>
	import {page} from "$app/stores"
	import {emojis} from "../emojis.js"
	
</script>

<h1>{$page.status} {$page.error.message}</h1>
<span>
	{emojis[$page.status] ?? emojis[500]}
</span>
```