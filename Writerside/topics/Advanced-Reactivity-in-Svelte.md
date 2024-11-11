# Advanced Reactivity in Svelte

State is deeply reactive, if you (for example) change a property of an object, or push to an array, it will cause the 
UI to update. This works by creating a proxy that intercepts reads and writes.

Occasionally, that’s not what you want. If you’re not changing individual properties, or if it’s important to main 
referential equality, then you can use raw state instead.

## Raw state

## Reactive classes

It’s not just variables that can be made reactive — in Svelte, we can also make properties of classes reactive.

```Typescript
class Box {
	width = $state(0);
	height = $state(0);
	area = $derived(this.width * this.height);

	constructor(width, height) {
		this.width = width;
		this.height = height;
	}

	embiggen(amount) {
		this.width += amount;
		this.height += amount;
	}
}
```

## Reactive built ins

Svelte ships with several reactive classes that you can use in place of JavaScript built-in objects — namely Map, Set, 
Date, URL and URLSearchParams.

We could declare date using $state(new Date()) and reassign it inside the setInterval. But a nicer 
alternative is to use SvelteDate from svelte/reactivity