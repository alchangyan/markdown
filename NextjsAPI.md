# My Own API for Next.js
## Global

project must have "page" folder, that will contains files as same names as our pages.
## Link (HOC)

```jsx
import Link from 'next/link';

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
                           // but currently we located on /about(about.js) page
  hash: 'title-1' // some hash(#) params
}

const handleClick = () => Router.push(href, as);

<button onClick={handleClick}>Go to /about/zeit</button>
```


## Layouts

We can simply create folder with layouts to wrap our pages.

We can do thta like we always do this in Lovely <3 ReactJS:

```jsx
<div style={layoutStyle}>
  <Header />
  {props.children}
</div>
```

and then  we wrap page like this:

```jsx
import Layout from '../components/Layout.js'

export default () => (
    <Layout>
       <p>Hello Next.js</p>
    </Layout>
)
```

or we can do the same another:

```jsx
import withLayout from '../components/Layout.js'

const Page = () => (
  <p>This is the about page</p>
)

export default withLayout(Page)
```

or 

```jsx
import withLayout from '../components/Layout.js'

const Page = () => (
  <p>This is the about page</p>
)

export default () => (<Layout page={Page}/>)
```

or maybe

```jsx
import withLayout from '../components/Layout.js'

const content = (<p>This is the about page</p>)

export default () => (<Layout content={content}/>)
```