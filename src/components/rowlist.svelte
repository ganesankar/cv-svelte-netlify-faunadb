<script>
  import Divider from "./divider.svelte";
  export let content;
</script>

<div class="full-width">

  {#each content.values as item (item.id)}
    {#if item.startdate}
      <Divider {item} type="date" />
    {/if}
    {#if item.name}
      <h3 className="text-primary">{item.name}</h3>
    {/if}
    {#if item.institute}
      <h4>{item.institute}</h4>
    {/if}
    {#if item.location}
      <p>{item.location}</p>
    {/if}
    {#if item.desc}
      <p>{item.desc}</p>
    {/if}
    {#if item.link || item.portfolio}
      <Divider {item} type="link" />
    {/if}
  {/each}

</div>
