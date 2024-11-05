# Logic in Svelte

HTML doesn’t have a way of expressing logic, like conditionals and loops. Svelte does.

To conditionally render some markup, we wrap it in an if block

## If block

```Typescript
<script>
	let count = $state(0);

	function increment() {
		count += 1;
	}
</script>

<button onclick={increment}>
	Clicked {count}
	{count === 1 ? 'time' : 'times'}
</button>

{#if count > 10}
<p>{count} is greater than 10</p>
{/if}
```

## Else blocks

Just like in JavaScript, an if block can have an else block

```Typescript
{#if count > 10}
	<p>{count} is greater than 10</p>
{:else}
	<p>{count} is between 0 and 10</p>
{/if}
```

## Else if blocks

```Typescript
{#if count > 10}
<p>{count} is greater than 10</p>
{:else if count < 5}
<p>{count} is less than 10</p>
{:else}
<p>{count} is between 5 and 10</p>
{/if}
```

## Each blocks

When building user interfaces you’ll often find yourself working with lists of data. In this exercise, we’ve repeated 
the button markup multiple times — changing the colour each time — but there’s still more to add.

Instead of laboriously copying, pasting and editing, we can get rid of all but the first button, then use an each block

```Typescript
<div>
	{#each colors as color}
		<button
			style="background: {color}"
			aria-label="{color}"
			aria-current={selected === color}
			onclick={() => selected = color}
		></button>
	{/each}
</div>
```

You can get the current index as a second argument, like so:

```Typescript
<div>
	{#each colors as color, i}
		<button
			style="background: {color}"
			aria-label="{color}"
			aria-current={selected === color}
			onclick={() => selected = color}
		> {i + 1} </button>
	{/each}
</div>
```

## Keyed each blocks

By default, when you modify the value of an each block, it will add and remove DOM nodes at the end of the block, and 
update any values that have changed. That might not be what you want.

```Typescript
{#each things as thing (thing.id)}
    <Thing name={thing.name} />
{/each}
```

## Await blocks

Most web applications have to deal with asynchronous data at some point. Svelte makes it easy to await the value of 
promises directly in your markup

```Typescript
<script>
	import { roll } from './utils.js';
	let promise = $state(roll());
</script>

<button onclick={() => promise = roll()}>
	roll the dice
</button>

{#await promise}
    <p>...rolling</p>
{:then number}
    <p>You rolled a {number}</p>
{:catch error}
    <p>{error.message}</p>
{/await}
```