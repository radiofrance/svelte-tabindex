<script>
  import { setContext } from 'svelte';
  import { writable } from 'svelte/store';
  import { contextKey } from './index';

  export let active = true;
  let state = writable(getAttributes(active));
  setContext(contextKey, state);

  $: $state = getAttributes(active);

  function getAttributes(active = true) {
    let tabindex = active ? -1 : null;
    return {
      tabindex
    };
  }
</script>

<slot />
