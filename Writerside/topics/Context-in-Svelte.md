# Context in Svelte

The context API provides a mechanism for components to ‘talk’ to each other without passing around data and functions 
as props, or dispatching lots of events. It’s an advanced feature, but a useful one. 

```Typescript
import { setContext } from 'svelte';
import { SvelteSet } from 'svelte/reactivity';

let { width = 100, height = 100, children } = $props();

let canvas;
let items = new SvelteSet();

setContext('canvas', { addItem });

function addItem(fn) {
    $effect(() => {
        items.add(fn);
        return () => items.delete(fn);
    });
}
```

```Typescript
import { getContext } from 'svelte';

let { x, y, size, rotate } = $props();

getContext('canvas').addItem(draw);
```