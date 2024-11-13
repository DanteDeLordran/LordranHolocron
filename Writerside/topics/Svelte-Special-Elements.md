# Svelte Special Elements


## Svelte window

Just as you can add event listeners to any DOM element, you can add event listeners to the window object with
'svelte:window'.

```Typescript
<script>
	let key = $state();
	let keyCode = $state();

	function onkeydown(event) {
		key = event.key;
		keyCode = event.keyCode;
	}
</script>

<svelte:window {onkeydown}/>

<div style="text-align: center">
	{#if key}
		<kbd>{key === ' ' ? 'Space' : key}</kbd>
		<p>{keyCode}</p>
	{:else}
		<p>Focus this window and press any key</p>
	{/if}
</div>
```

### bindings

We can also bind to certain properties of window, such as scrollY

```Typescript
<script>
	let y = $state(0);
</script>

<svelte:window bind:scrollY={y} />

<span>depth: {y}px</span>
```

The list of properties you can bind to is as follows:

- innerWidth
- innerHeight
- outerWidth
- outerHeight
- scrollX
- scrollY
- online — an alias for window.navigator.onLine

All except scrollX and scrollY are readonly.

## Svelte body

Similar to ```svelte:window``` and ```svelte:document```, the ```svelte:body``` element allows you to listen for events 
that fire on document.body. This is useful with the mouseenter and mouseleave events, which don’t fire on window

```Typescript
<script>
	import kitten from './kitten.png';

	let hereKitty = $state(false);
</script>

<svelte:body 
    onmouseenter={() => hereKitty = true} 
    onmouseleave={() => hereKitty = false}
/>

<img
	class:curious={hereKitty}
	alt="Kitten wants to know what's going on"
	src={kitten}
/>
```

## Svelte head

The 'svelte:head' element allows you to insert elements inside the 'head' of your document. This is useful for things 
like 'title' and 'meta' tags, which are critical for good SEO.

```HTML
<svelte:head>
	<link rel="stylesheet" href="/tutorial/stylesheets/{selected}.css" />
</svelte:head>
```