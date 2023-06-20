<script>
  import dictionary from '@/data/dictionary.json';

  export let db;
</script>

<section class="technical-skills">
  <div class="title">{dictionary.technicalSkills}</div>
  {#each db as skill}
    <dl>
      <dt>{skill.title}</dt>
      <dd>{skill.description}</dd>
    </dl>
  {/each}
</section>

<style lang="scss">
  @use "@/styles/global";

  section.technical-skills {
    @include global.description-list();
  }
</style>
