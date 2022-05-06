<script>
  import { setContext } from 'svelte'
  import {writable} from 'svelte/store';
  import { key } from '../lib/context'

  export let active = true
  let state = writable(getAttributes(active))
  setContext(key, state);

  $: $state = getAttributes(active)

  function getAttributes(active = true) {
    let tabindex = active ? -1 : null
    return {
      tabindex,
    }
  }

</script>

<slot />