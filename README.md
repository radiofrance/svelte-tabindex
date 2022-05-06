# svelte-tabindex

A Svelte component for managing tabindex.

## Installation

`npm install svelte-tabindex`

## How does it works ?
`<NoTab>...</NoTab>` creates a reactive svelte context (using `writable`) so that its children can update their tabindex.

Every fousable element of your app (links, buttons, inputs ...) must get the context to implement this behaviour.

The context value is an object (`{ tabindex : Number }`) you can spread as node attribute to do so.
## Usage

__Link.svelte__ _(a simple link wrapper that gets the svelte-tabindex context)_
```html
<script>
  import { getContext } from 'svelte'
  import { key } from 'svelte-tabindex/context.js'

  export let href = ''
  let tabindexAttr = getContext(key)
</script>

<a {href} {...$tabindexAttr}><slot/></a>
```

__App.svelte__
```html
<script>
    import Link from './Link.svelte'
    import NoTab from 'svelte-tabindex/NoTab.svelte'
</script>

<Link href='/'>focusable link</Link>
<NoTab>
    <Link href='/'>non focusable link</Link>
    <Link href='/'>another non focusable link</Link>
</NoTab>
<Link href='/'>another focusable link</Link>
```

## Advanced usage

The `<NoTab>` component has an `active` (Boolean) attribute witch can be used to disable its behaviour.