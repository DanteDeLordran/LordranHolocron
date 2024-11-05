# Bindings in Svelte


## Text inputs

As a general rule, data flow in Svelte is top down — a parent component can set props on a child component, and a component can set attributes on an element, but not the other way around.

Sometimes it’s useful to break that rule. Take the case of the 'input' element in this component — we could add an 'oninput' event handler that sets the value of name to event.target.value, but it’s a bit... boilerplatey. It gets even worse with other form elements, as we’ll see.

Instead, we can use the bind:value directive

```Typescript
<script>
	let name = $state('world');
</script>

<input bind:value={name} />

<h1>Hello {name}!</h1>
```


## Numeric inputs

In the DOM, every input value is a string. That’s unhelpful when you’re dealing with numeric inputs — type="number" and type="range" — as it means you have to remember to coerce input.value before using it.

With bind:value, Svelte takes care of it for you

```Typescript
<script>
	let a = $state(1);
	let b = $state(2);
</script>

<label>
	<input type="number" bind:value={a} min="0" max="10" />
	<input type="range" bind:value={a} min="0" max="10" />
</label>

<label>
	<input type="number" bind:value={b} min="0" max="10" />
	<input type="range" bind:value={b} min="0" max="10" />
</label>

<p>{a} + {b} = {a + b}</p>
```

## Checkbox inputs

Checkboxes are used for toggling between states. Instead of binding to input.value, we bind to input.checked

```Typescript
<script>
	let yes = $state(false);
</script>

<label>
	<input type="checkbox" bind:checked={yes} />
	Yes! Send me regular email spam
</label>

{#if yes}
	<p>
		Thank you. We will bombard your inbox and sell
		your personal details.
	</p>
{:else}
	<p>
		You must opt in to continue. If you're not
		paying, you're the product.
	</p>
{/if}

<button disabled={!yes}>Subscribe</button>
```

## Select bindings

You can also declare event handlers inline

```Typescript
<script>
	let questions = $state([
		{
			id: 1,
			text: `Where did you go to school?`
		},
		{
			id: 2,
			text: `What is your mother's name?`
		},
		{
			id: 3,
			text: `What is another personal find with Google?`
		}
	]);

	let selected = $state();

	let answer = $state('');

	function handleSubmit(e) {
		e.preventDefault();
		alert(
			`answered ${selected.id} (${selected.text}) with "${answer}"`
		);
	}
</script>

<h2>Insecurity questions</h2>

<form onsubmit={handleSubmit}>
	<select
		bind:value={selected}
		onchange={() => (answer = '')}
	>
		{#each questions as question}
			<option value={question}>
				{question.text}
			</option>
		{/each}
	</select>

	<input bind:value={answer} />

	<button disabled={!answer} type="submit">
		Submit
	</button>
</form>

<p>
	selected question {selected
		? selected.id
		: '[waiting...]'}
</p>
```

## Group inputs

If you have multiple type="radio" or type="checkbox" inputs relating to the same value, you can use bind:group 
along with the value attribute. Radio inputs in the same group are mutually exclusive; checkbox inputs in the same 
group form an array of selected values.

```Typescript
<script>
	let scoops = $state(1);
	let flavours = $state([]);

	const formatter = new Intl.ListFormat('en', { style: 'long', type: 'conjunction' })
</script>

<h2>Size</h2>

{#each [1, 2, 3] as number}
	<label>
		<input
			type="radio"
			name="scoops"
			value={number}
			bind:group={scoops}
		/>

		{number} {number === 1 ? 'scoop' : 'scoops'}
	</label>
{/each}

<h2>Flavours</h2>

{#each ['cookies and cream', 'choc chip', 'raspberry'] as flavour}
	<label>
		<input
			type="checkbox"
			name="flavours"
			value={flavour}
			bind:group={flavours}
		/>

		{flavour}
	</label>
{/each}

{#if flavours.length === 0}
	<p>Please select at least one flavour</p>
{:else if flavours.length > scoops}
	<p>Can't order more flavours than scoops!</p>
{:else}
	<p>
		You ordered {scoops} {scoops === 1 ? 'scoop' : 'scoops'}
		of {formatter.format(flavours)}
	</p>
{/if}

```


## Multiple select

A 'select' element can have a multiple attribute, in which case it will populate an array rather than selecting a 
single value

```Typescript
<select multiple bind:value={flavours} >
	{#each ['cookies and cream', 'choc chip', 'raspberry'] as flavour}
		<option>{flavour}</option>
	{/each}
</select>
```
