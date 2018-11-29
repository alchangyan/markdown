# My Own API for Next.js

## Link (HOC)

```jsx
<Link href="/about">
  <a>go to about page</a>
</Link>
```

or

```jsx
<Link href="/about">
  <button>go to about page</button>
</Link>
```

Link HOC supports all components with onClick attribute(method)

use "prefetch" for previously load/compile future page

```jsx
<Link prefetch href="/">
```

also can be used next example:

current location is /about
```jsx
const href = {
  pathname: '/about', // the location where we want to go and this means,
                      // that in this example we want to stay at the same location,
                      // but we need to change props of "new loaded" component
  query: { name: 'zeit' } // some data to send to our new implemented /about page
}

const as = {
  pathname: '/about/zeit', // here is what we will see in URL string -> /about/zeit,
                           // but currently we located on /about page
  hash: 'title-1' // some hash(#) params
}

const handleClick = () => Router.push(href, as)

<button onClick={handleClick}>Go to /about/zeit</button>
```
