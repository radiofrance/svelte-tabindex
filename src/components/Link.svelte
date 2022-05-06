<script>
  import { getContext } from 'svelte'
  import { key } from '../contexts/notab'

  export let href = ''
  let linkAttributes = getContext(key)
</script>

<a {href} {...$linkAttributes}><slot/></a>