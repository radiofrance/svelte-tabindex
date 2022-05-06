<script>
  import { getContext } from 'svelte';
  import { contextKey } from '../lib/index';

  export let href = '';
  let tabindexAttr = getContext(contextKey);
</script>

<a {href} {...$tabindexAttr}><slot /></a>
