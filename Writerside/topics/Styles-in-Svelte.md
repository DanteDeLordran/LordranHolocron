# Styles in Svelte

Like any other attribute, you can specify classes with a JavaScript attribute

## The class directive

You can also declare event handlers inline

```Typescript
<button 
    class="card {flipped ? 'flipped' : ''}"
    onclick={() => flipped = !flipped} 
>
```

## The style directive

As with class, you can write your inline style attributes literally, because Svelte is really just HTML with fancy bits

```Typescript
<button
	class="card"
	style="transform: {flipped ? 'rotateY(0)' : ''}; --bg-1: palegoldenrod; --bg-2: black; --bg-3: goldenrod"
	onclick={() => flipped = !flipped}
>
```

When you have a lot of styles, it can start to look a bit wacky. We can tidy things up by using the style: directive

```Typescript
<button
	class="card"
	style:transform={flipped ? 'rotateY(0)' : ''}
	style:--bg-1="palegoldenrod"
	style:--bg-2="black"
	style:--bg-3="goldenrod"
	onclick={() => flipped = !flipped}
>
```
