# Events in Svelte

As we’ve briefly seen already, you can listen to any DOM event on an element (such as click or pointermove) with an 
on function

## DOM events

```Typescript
<script>
	let m = $state({ x: 0, y: 0 });

	function onpointermove(event) {
		m.x = event.clientX;
		m.y = event.clientY;
	}
</script>

<div {onpointermove}>
	The pointer is at {Math.round(m.x)} x {Math.round(m.y)}
</div>
```

## Inline handlers

You can also declare event handlers inline

```Typescript
<div onpointermove = {(event) => {
		m.x = event.clientX;
		m.y = event.clientY;
	}}>
	The pointer is at {Math.round(m.x)} x {Math.round(m.y)}
</div>
```


## Component events

You can pass event handlers to components like any other prop. In Stepper.svelte, add increment and decrement props...

```Typescript
// Stepper.svelte
<script>
	let {increment, decrement} = $props();
</script>

<button onclick={decrement} >-1</button>
<button onclick={increment} >+1</button>
```

```Typescript
// App.svelte
<script>
	import Stepper from './Stepper.svelte';

	let value = $state(0);
</script>

<p>The current value is {value}</p>

<Stepper 
	increment={() => value += 1}
	decrement={() => value -= 1}
/>

```