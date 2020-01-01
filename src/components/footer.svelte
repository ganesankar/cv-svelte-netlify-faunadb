<script>
  export let active = false;
  export const build = [
    {
      name: "Frameworks",
      address: "svelte, bulma, Nuxt.js"
    },
    {
      name: "Library",
      address: "Luxon"
    },
    {
      name: "Server",
      address: "Netlify, Lambda"
    },
    {
      name: "CDN",
      address: "Netlify"
    },
    {
      name: "Database",
      address: "FaunaDB"
    },
    {
      name: "Others",
      address: "Webpack, Normalize, ESLint, ScSS"
    }
  ];
  function handleClick() {
    active = active ? false : true;
  }
</script>

<div class="">
  <div class="modal {active === true ? 'is-active' : ''}">
    <div class="modal-background" />
    <div class="modal-card">
      <header class="modal-card-head">
        <p class="modal-card-title">Built With</p>
        <button on:click={handleClick} class="delete" aria-label="close" />
      </header>
      <section class="modal-card-body">
        <table class="table is-fullwidth">

          <tbody>

            {#each build as item}
              <tr>
                <th>{item.name}</th>
                <td>{item.address}</td>
              </tr>
            {/each}
          </tbody>
        </table>

      </section>
      <footer class="modal-card-foot" />
    </div>
  </div>
  <footer class="footer">
    <div class="content has-text-centered">

      <strong>&copy; {new Date().getFullYear()} Ganesan Karuppaiya</strong>
      <br />
      <button class="button is-text" on:click={handleClick}>Info</button>

    </div>
  </footer>
</div>
