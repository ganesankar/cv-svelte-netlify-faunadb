<script>
  import { onMount, afterUpdate } from "svelte";
  import Navbar from "./components/nav.svelte";
  import ColumnList from "./components/columnlist.svelte";
  import RowList from "./components/rowlist.svelte";
  import CardList from "./components/cardlist.svelte";
  import GroupByList from "./components/groupby.svelte";
  import ProgressBarList from "./components/progressbar.svelte";
  import Preloader from "./components/preloader.svelte";
  import Hero from "./components/hero.svelte";
  import Footer from "./components/footer.svelte";
  let content = [];

  onMount(async () => {
    const response = await fetch(
      "https://ganesan-cv-reactjs.netlify.app/.netlify/functions/cv-all"
    );
    const contentbase = await response.json();
    const contentdata = [];
    contentbase.forEach(function(item, index) {
      contentdata.push(item.data);
    });
    content = contentdata.sort((a, b) =>
      a.id > b.id ? 1 : b.id > a.id ? -1 : 0
    );
  });
</script>

<main>
  <Navbar {content} />

  {#if content.length > 0}
    {#each content as item (item.id)}
      <div class="container-fluid" id={item.type}>
        <div class="container">

          <div class="columns">
            <div class="column titleLeft">
              {#if item.type == 'intro'}
                <p />
              {:else if item.type == 'social'}
                <Hero title="SOCIAL" subtitle="Kindof Active" />
              {:else if item.type == 'contacts'}
                <Hero title="CONTACTS" subtitle="Ways to reach me" />
              {:else}
                <Hero title={item.name} subtitle={item.desc} />
              {/if}
            </div>
            <div class="column is-three-quarters rightContainer">
              <div class="">
                {#if item.type == 'intro'}
                  <div class="full-width">
                    <Hero title={item.name} subtitle="" />
                    <p>
                      {@html item.desc}
                    </p>
                  </div>
                {:else if item.type == 'social' || item.type == 'contacts' || item.type == 'profile'}
                  <ColumnList content={item} />
                {:else if item.type == 'education' || item.type == 'awards' || item.type == 'otherprojects'}
                  <RowList content={item} />
                {:else if item.type == 'experience' || item.type == 'projects'}
                  <CardList content={item} />
                {:else if item.type == 'expertise'}
                  <GroupByList content={item} key="desc" />
                {:else if item.type == 'skills'}
                  <ProgressBarList content={item} />
                {:else}
                  <p>is between 5 and 10</p>
                {/if}
              </div>
            </div>
          </div>
        </div>
      </div>
    {/each}
  {:else}
    <Preloader position="absolute" />
  {/if}
  <Footer />
</main>
