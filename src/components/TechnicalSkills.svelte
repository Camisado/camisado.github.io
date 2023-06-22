<script>
  import dictionary from '@/data/dictionary.json';

  export let db;
</script>

<section class="technical-skills">
  <div class="title">{dictionary.technicalSkills}</div>
  {#each db as skill}
    <dl>
      <dt>{skill.title}</dt>
      <dd>{skill.description.join(', ')}</dd>
    </dl>
  {/each}
</section>

<style lang="scss">
  @use "@/styles/mixins";

  section.technical-skills {
    @include mixins.description-list();
  }
</style>
