# Actions in Svelte

Start typing here...

## Else blocks

Just like in JavaScript, an if block can have an else block

```Typescript
{#if count > 10}
	<p>{count} is greater than 10</p>
{:else}
	<p>{count} is between 0 and 10</p>
{/if}
```