<script>
  import NoTab from '../lib/NoTab.svelte';
  import Link from '../components/Link.svelte';

  const items = Array(3)
    .fill(0)
    .map((_, i) => i + 1);
  let toggle0 = true;
  let toggle1 = true
</script>

<h1>focusable</h1>
<ul>
{#each items as item}
  <li>
    <Link href="/">Link {item}</Link>
  </li>
{/each}
</ul>

<h1><input type="checkbox" bind:checked={toggle0} />NoTab active : {toggle0}</h1>
<NoTab active={toggle0}>
  <ul>
  {#each items as item, index}
    <li>
      <Link href="/">Link {item}</Link>
      {#if index === 2}
        <h2><input type="checkbox" bind:checked={toggle1} /> Nested NoTab active : {toggle1}</h2>
        <NoTab active={toggle1}>
          <ul>
            {#each items as item1}
            <li>
              <Link href="/">Link {item1}</Link>
            </li>
            {/each}
          </ul>
        </NoTab>

        <h2>Nested NoTab reset</h2>
        <NoTab reset>
          <ul>
            {#each items as item1}
            <li>
              <Link href="/">Always focusable nested Link {item1}</Link>
            </li>
            {/each}
          </ul>
        </NoTab>
      {/if}
    </li>
  {/each}
  </ul>
</NoTab>

<h1>focusable again</h1>
<ul>
{#each items as item}
  <li>
    <Link href="/">Link {item}</Link>
  </li>
{/each}
</ul>

<style>
  input[type='checkbox'] {
    width: 20px;
    height: 20px;
  }
  ul {
    border: 1px solid grey;
    padding: 20px 20px;
  }
</style>
