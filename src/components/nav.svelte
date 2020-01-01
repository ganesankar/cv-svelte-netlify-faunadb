<script>
  export let content;
</script>

<main>
  <nav class="navbar" role="navigation" aria-label="main navigation">
    <div class="navbar-brand">
      <a class="navbar-item" href="/"> Ganesan Karuppaiya</a>
    </div>
    <div id="navbarBasicExample" class="navbar-menu">
      <div class="navbar-end">
        <div class="navbar-item has-dropdown is-hoverable">
          <a
            href="#/"
            class="navbar-burger burger navbar-link button is-primary">
            <span aria-hidden="true" />
            <span aria-hidden="true" />
            <span aria-hidden="true" />
          </a>
          <div class="navbar-dropdown is-right">
            {#each content as item (item.id)}
              <a href="#{item.type}" class="navbar-item">{item.type}</a>
            {/each}
          </div>
        </div>
      </div>
    </div>
  </nav>
</main>
