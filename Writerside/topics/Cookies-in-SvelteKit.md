# Cookies in SvelteKit

In your load functions, you can read a cookie with cookies.get(name, options)

```TypeScript
export function load({cookies}) {
    const visited = cookies.get('visited')
	cookies.set('visited','true', {path: '/'})
	return {
		visited: visited === 'true'
	};
}
```

Calling cookies.set(name, ...) causes a Set-Cookie header to be written, but it also updates the internal map of 
cookies, meaning any subsequent calls to cookies.get(name) during the same request will return the updated value.

