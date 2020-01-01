<script>
  import { DateTime } from "luxon";
  import { fade, fly } from "svelte/transition";
  export let content;
  content.values.forEach(function(item) {
    item.respShow = false;
    
  });
</script>

<main>

  {#each content.values as item }
    <div class="card" ck>
      <header class="card-header">
        <div class="card-header-title">
          <h3>{item.name}</h3>
        </div>
        <span class="card-header-icon" aria-label="more options">

          {#if item.startdate == 'c'}
            Present
          {:else}
            {DateTime.fromFormat(item.startdate, 'dd/mm/yyyy').toFormat('MMM yyyy')}
          {/if}
          -
          {#if item.enddate == 'c'}
            Present
          {:else}
            {DateTime.fromFormat(item.enddate, 'dd/mm/yyyy').toFormat('MMM yyyy')}
          {/if}
        </span>
      </header>
      <footer class="card-footer first">
        {#if item.client}
          <span class="card-footer-item">{item.client}</span>
        {/if}
        <span class="card-footer-item">
          {item.company}
          {#if item.location}- {item.location}{/if}
        </span>

      </footer>
      <div class="card-content">
        <div class="content">{item.desc}</div>

      </div>
      {#if item.technology}
        <footer class="card-footer ">
          <span class="card-footer-item align-left">Technology</span>
        </footer>
        <div class="card-content">
          <div class="content">
            {#each item.technology as itemp}
              <span class="tag is-info">{itemp}</span>
              &nbsp;
            {/each}
          </div>

        </div>
      {/if}

      {#if item.values}
        <footer class="card-footer ">
          <span class="card-footer-item align-left">
            <label class="checkbox c1">
              <input type="checkbox" bind:checked={item.respShow} />
              Responsibility
            </label>
          </span>
        </footer>
        {#if item.respShow}
          <div class="card-content" in:fade out:fade>
            <ol>
              {#each item.values as itemp}
                <li>{itemp.name}</li>
                &nbsp;
              {/each}
            </ol>

          </div>
        {/if}
      {/if}
    </div>
    <br />
  {/each}

</main>
