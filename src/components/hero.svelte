<script>
  export let title;
  export let subtitle;
</script>

<section class="hero">
  <div class="hero-body">
    <div class="container">
     {#if title}
        <h1 class="title">{title}</h1>
      {/if}
      
      {#if subtitle}
        <h2 class="subtitle">{subtitle}</h2>
      {/if}
    </div>
  </div>
</section>
