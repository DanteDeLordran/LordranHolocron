# Forms in SvelteKit

In the chapter on loading data, we saw how to get data from the server to the browser. Sometimes you need to send 
data in the opposite direction, and that’s where 'form' — the web platform’s way of submitting data — comes in.

```TypeScript
export const actions = {
    default: async ({cookies, request}) => {
        const data = await request.formData()
        db.createTodo(cookies.get('userid'), data.get('description'))
    }
}
```

```HTML
<form method="POST">
	<label>
		add a todo:
		<input name="description" autocomplete="off"/>
	</label>
</form>
```

## Named form actions

```HTML

<script>
    let { data } = $props();
</script>

<div class="centered">
	<h1>todos</h1>

	<form method="POST" action="?/create">
		<label>
			add a todo:
			<input
				name="description"
				autocomplete="off"
			/>
		</label>
	</form>

	<ul class="todos">
		{#each data.todos as todo (todo.id)}
			<li>
				<form method="POST" action="?/delete">
					<input type="hidden" name="id" value={todo.id} />
					{todo.description}
					<button aria-label="Mark as complete"></button>
				</form>
			</li>
		{/each}
	</ul>
</div>
```

```TypeScript
export const actions = {
	create: async ({ cookies, request }) => {
		const data = await request.formData();
		db.createTodo(cookies.get('userid'), data.get('description'));
	},
	delete: async ({cookies, request}) => {
		const data = await request.formData()
		db.deleteTodo(cookies.get('userid'), data.get('id'))
	}
};
```

## Form validation

Users are a mischievous bunch, who will submit all kinds of nonsensical data if given the chance. To prevent them from 
causing chaos, it’s important to validate form data.

The first line of defense is the browser’s built-in form validation, which makes it easy to, for example, mark an 
'input' as required

```
<form method="POST" action="?/create">
	<label>
		add a todo:
		<input
			name="description"
			autocomplete="off"
			required
		/>
	</label>
</form>
```


This kind of validation is helpful, but insufficient. Some validation rules (e.g. uniqueness) can’t be expressed using 
'input' attributes, and in any case, if the user is an elite hacker they might simply delete the attributes using the 
browser’s devtools. To guard against these sorts of shenanigans, you should always use server-side validation

```TypeScript
create: async ({ cookies, request }) => {
	const data = await request.formData();
	try {
		db.createTodo(cookies.get('userid'), data.get('description'));
	} catch (error) {
		return fail(422, {
			description: data.get('description'),
			error: error.message
		})
	}	
},
```

```HTML
<script>
	let { data, form } = $props();
</script>

<div class="centered">
	<h1>todos</h1>

	{#if form?.error}
		<p>{form.error}</p>
	{/if}

	<form method="POST" action="?/create">
		<label>
			add a todo:
			<input
				name="description"
				autocomplete="off"
				required
				value={form?.description ?? ''}
			/>
		</label>
	</form>
```

## Progressive enhancement

Because we’re using 'form', our app works even if the user doesn’t have JavaScript (which happens more often than you
probably think). That’s great, because it means our app is resilient.

Most of the time, users do have JavaScript. In those cases, we can progressively enhance the experience, the same 
way SvelteKit progressively enhances 'a' elements by using client-side routing.

Now, when JavaScript is enabled, use:enhance will emulate the browser-native behaviour except for the full-page reloads. It will:

- update the form prop
- invalidate all data on a successful response, causing load functions to re-run
- navigate to the new page on a redirect response
- render the nearest error page if an error occurs

Now that we’re updating the page rather than reloading it, we can get fancy with things like transitions: