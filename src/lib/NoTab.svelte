<script>
  import { setContext, getContext } from 'svelte';
  import { writable } from 'svelte/store';
  import { contextKey } from './index';

  export let active = true;
  export let reset = false
  
  let parentContext = getContext(contextKey);
  $: parentActive = Boolean($parentContext?.tabindex)
  let state = writable(getAttributes(active, parentActive, reset));
  setContext(contextKey, state);
  
  $: $state = getAttributes(active, parentActive, reset);
  
  // if any parent is active, this is active
  function getAttributes(active = true, parentActive = false, reset = false) {
    if (reset) {
      return { tabindex: null };
    }
    let tabindex = (active || parentActive) ? -1 : null;
    return { tabindex };
  }
</script>

<slot />
