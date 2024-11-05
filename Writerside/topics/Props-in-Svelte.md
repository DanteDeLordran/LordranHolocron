# Props in Svelte

In any real application, you’ll need to pass data from one component down to its children. To do that, we need to 
declare properties, generally shortened to ‘props’. In Svelte, we do that with the ```$props``` rune

```Typescript
let { answer } = $props()
```

## Default values

We can easily specify default values for props

```Typescript
let { answer = 'a mistery' } = $props();
```

## Spread props

Since the properties of pkg correspond to the component’s expected props, we can ‘spread’ them onto the component instead

```Typescript
<script>
	import PackageInfo from './PackageInfo.svelte';

	const pkg = {
		name: 'svelte',
		version: 5,
		description: 'blazing fast',
		website: 'https://svelte.dev'
	};
</script>

<PackageInfo {...pkg} />
```