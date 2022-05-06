# svelte-tabindex

A Svelte component for managing tabindex.

## Installation

`npm install svelte-tabindex`

## How does it works ?

`<NoTab>...</NoTab>` creates a reactive svelte context (using `writable`) so that its children can update their tabindex.

Every fousable element of your app (links, buttons, inputs ...) must get the context to implement this behaviour.

The context value is an object (`{ tabindex : Number }`) you can spread as node attribute to do so.

## Usage

**Link.svelte** _(a simple link wrapper that gets the svelte-tabindex context)_

```html
<script>
  import { getContext } from 'svelte';
  import { contextKey } from 'svelte-tabindex';

  export let href = '';
  let tabindexAttr = getContext(contextKey);
</script>

<a {href} {...$tabindexAttr}><slot /></a>
```

**App.svelte**

```html
<script>
    import Link from './Link.svelte'
    import { NoTab } from 'svelte-tabindex'
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
