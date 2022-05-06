<script>
  import { getContext } from 'svelte'
  import { key } from '../lib/context'

  export let href = ''
  let tabindexAttr = getContext(key)
</script>

<a {href} {...$tabindexAttr}><slot/></a>