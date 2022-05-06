<script>
  import NoTab from '../lib/NoTab.svelte';
  import Link from '../components/Link.svelte';

  const items = Array(3)
    .fill(0)
    .map((_, i) => i + 1);
  let focusableToggle = true;
</script>

<h1>focusable</h1>
{#each items as item}
  <li>
    <Link href="/">Link {item}</Link>
  </li>
{/each}

<h1><input type="checkbox" bind:checked={focusableToggle} />NoTab active : {focusableToggle}</h1>
<NoTab active={focusableToggle}>
  {#each items as item}
    <li>
      <Link href="/">Link {item}</Link>
    </li>
  {/each}
</NoTab>

<h1>focusable again</h1>
{#each items as item}
  <li>
    <Link href="/">Link {item}</Link>
  </li>
{/each}

<style>
  input[type='checkbox'] {
    width: 20px;
    height: 20px;
  }
</style>
