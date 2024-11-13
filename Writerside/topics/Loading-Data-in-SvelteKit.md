# Loading Data in SvelteKit

Start typing here...

## Page Data

Every page of your app can declare a load function in a +page.server.js file alongside the +page.svelte file. As the 
file name suggests, this module only ever runs on the server, including for client-side navigations.

```TypeScript
import { posts } from './data.js';

export function load() {
    return {
        summaries: posts.map((post) => ({
            slug: post.slug,
            title: post.title
        }))
    };
}
```

```TypeScript
<script>
	let { data } = $props();
</script>

<ul>
	{#each data.summaries as { slug, title }}
		<li><a href="/blog/{slug}">{title}</a></li>
	{/each}
</ul>
```

## Layout Data

The layout (and any page below it) inherits data.summaries from the parent +layout.server.js.