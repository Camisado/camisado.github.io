<script>
  import dictionary from '@/data/dictionary.json';

  export let db;
</script>

<section class="education">
  <div class="title">{dictionary.education}</div>
  {#each db as education}
    <dl>
      <dt>{education.title}</dt>
      <dd>
        <div>{education.place}</div>
        <div>{education.duration}</div>
      </dd>
    </dl>
  {/each}

</section>

<style lang="scss">
  @use "@/styles/global";

  section.education {
    @include global.description-list();
  }
</style>
