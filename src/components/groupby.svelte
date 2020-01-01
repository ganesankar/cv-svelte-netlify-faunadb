<script>
  import { onMount } from "svelte";
  export let content;
  export let contentdata;
  export let key;

  onMount(async () => {
    let groupKey = key;
    if (content.values && content.values.length > 0) {
      let newcontentkey = [];
      let cs = [];
      content.values.forEach(function(item) {
        newcontentkey.push(item[groupKey]);
      });
      let uniqkey = Array.from(new Set(newcontentkey));
      uniqkey.forEach(function(item, index) {
        let newOb = { id: index, name: item, values: [] };
        content.values.forEach(function(j) {
          if (j[groupKey] == item) {
            newOb.values.push(j);
          }
        });
        cs.push(newOb);
      });
      contentdata = cs;
    }
  });
</script>

<div class="full-width">
  {#if contentdata}
    {#each contentdata as item (item.id)}
      <h6 class="title is-6">{item.name}</h6>
      <ol>
        {#each item.values as itemv (itemv.id)}
          <li>
            <h6 class="">{itemv.name}</h6>
            <div class="tags">
              {#each itemv.values as itemp}
                <span class="tag is-info">{itemp}</span>
              {/each}
            </div>
          </li>
        {/each}
      </ol>
    {/each}
  {/if}
</div>
