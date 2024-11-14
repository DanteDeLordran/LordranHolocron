# Stores in SvelteKit

Svelte stores are a place to put data that doesn’t belong to an individual component.

SvelteKit makes three readonly stores available via the $app/stores module — page, navigating and updated. The one you’ll use most often is page, which provides information about the current page:

## page

url — the URL of the current page
params — the current page’s parameters
route — an object with an id property representing the current route
status — the HTTP status code of the current page
error — the error object of the current page, if any (you’ll learn more about error handling in later exercises)
data — the data for the current page, combining the return values of all load functions
form — the data returned from a form action

```HTML
<script>
	import {page} from "$app/stores"
	
	let { children } = $props();
</script>

<nav>
	<a href="/" aria-current={$page.url.pathname === '/'}>
		home
	</a>

	<a href="/about" aria-current={$page.url.pathname === '/about'}>
		about
	</a>
</nav>

{@render children()}
```

## navigation

The navigating store represents the current navigation. When a navigation starts — because of a link click, or a back/forward navigation, or a programmatic goto — the value of navigating will become an object with the following properties:

- from and to — objects with params, route and url properties
- type — the type of navigation, e.g. link, popstate or goto

```HTML
<script>
	import { page, navigating } from '$app/stores';
	let { children } = $props();
</script>

<nav>
	<a href="/" aria-current={$page.url.pathname === '/'}>
		home
	</a>

	<a href="/about" aria-current={$page.url.pathname === '/about'}>
		about
	</a>

    {#if $navigating}
		navigating to {$navigating.to.url.pathname}
	{/if}

</nav>

{@render children()}
```
