<script>
  import { DateTime } from "luxon";
  export let item;
  export let type;
</script>

{#if item}
  <div class="el-divider">
    {#if type == 'date'}
      <div class="el-divider-text is-right">

        {#if item.startdate == 'c'}
          <span>Present</span>
        {:else}
          <span>
            {DateTime.fromFormat(item.startdate, 'dd/mm/yyyy').toFormat('MMM yyyy')}
          </span>
        {/if}
        -
        {#if item.enddate == 'c'}
          <span>Present</span>
        {:else}
          <span>
            {DateTime.fromFormat(item.enddate, 'dd/mm/yyyy').toFormat('MMM yyyy')}
          </span>
        {/if}

      </div>
    {/if}
    {#if type == 'link'}
      <div class="el-divider-text is-left">

        {#if item.portfolio}
          <a href={item.portfolio} target="_blank" class="is-text is-info">
            <i class={`fab  fa-lg ${item.icon}`} />
            &nbsp; {item.portfolio}
          </a>
        {:else if item.link}
          <a href={item.link} target="_blank" class="is-text is-info">
            <i class={`fab  fa-lg ${item.icon}`} />
            &nbsp; {item.name}
          </a>
        {/if}
      </div>
    {/if}
  </div>
{/if}
