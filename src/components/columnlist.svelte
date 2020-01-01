<script>
  export let content;
</script>

<div class="columns full-width">
  {#each content.values as item (item.id)}
    <div class="column">
      {#if item.link}
        <h4>{item.name}</h4>
        <a href={item.link} target="_blank" class="is-text is-info ">{item.desc}</a>
      {/if}
      {#if item.elink}
        <a href={item.elink} target="_blank" class="button is-info is-outlined">
          <i class={`fab  fa-lg ${item.icon}`} />
          &nbsp; {item.name}
        </a>
      {/if}
    </div>
  {/each}

</div>
