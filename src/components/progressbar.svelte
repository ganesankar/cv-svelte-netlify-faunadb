<script>
  export let content;
</script>

<div class="full-width">
  {#each content.values as item, i (item.id)}
    <div class="progresbarContent e_{(i %2 == 0)?'odd':'even'}">
      <h4> {item.percentage}% {item.name}</h4>
      <progress class="progress is-info is-small" value={item.percentage} max="100">
       {item.percentage}
      </progress>

    </div>
    
  {/each}

</div>
