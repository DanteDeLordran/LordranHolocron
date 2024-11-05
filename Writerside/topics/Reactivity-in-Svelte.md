# Reactivity in Svelte

## State

At the heart of Svelte is a powerful system of reactivity for keeping the DOM in sync with your application state — for 
example, in response to an event.

Make the count declaration reactive by wrapping the value with $state(...):

```Typescript
let count = $state(0);
```

This is called a rune, and it’s how you tell Svelte that count isn’t an ordinary variable. Runes look like functions, 
but they’re not — when you use Svelte, they’re part of the language itself.

All that’s left is to implement increment:

```Typescript
function increment() {
    count += 1;
}
```

### How to print reactive variables on console

```Typescript
let numbers = $state([1, 2, 3, 4]);
let total = $derived(numbers.reduce((t, n) => t + n, 0));

function addNumber() {
	numbers.push(numbers.length + 1);
	console.log($state.snapshot(numbers));
}
$inspect(numbers).with(console.trace)
```

## Effect

So far we’ve talked about reactivity in terms of state. But that’s only half of the equation — state is only reactive 
if something is reacting to it, otherwise it’s just a sparkling variable.

The thing that reacts is called an effect. You’ve already encountered effects — the ones that Svelte creates on your 
behalf to update the DOM in response to state changes — but you can also create your own with the $effect rune.

```Typescript
let elapsed = $state(0);
let interval = $state(1000);

$effect(() => {
    setInterval(() => {
        elapsed += 1;
    }, interval);
});
```

## Universal reactivity

We can also use runes outside components, for example to share some global state.

You can’t use runes in normal .js files, only .svelte.js files. 
Let’s fix that renaming the files to ```*.svelte.ts```