<script>
  import ExperienceRecord from '@/components/ExperienceRecord.svelte';
  import dictionary from '@/data/dictionary.json';

  export let db;
</script>

<section class="professional-experience">
  <div class="title">{dictionary.professionalExperience}</div>

  <div class="timeline">
    {#each db as record}
      <div class="timeline-item">
        <ExperienceRecord db={record} />
      </div>
    {/each}
  </div>
</section>

<style lang="scss">
  @use 'sass:map';
  @use '@/styles/theme';
  @use '@/styles/breakpoints';
  @use '@/styles/mixins';

  @mixin timeline-dot($src, $color) {
    content: '';
    @include mixins.masked-svg($src, $color,);
    position: absolute;
    top: 0;

    @include breakpoints.from(xs) {
      width: 12px;
      height: 12px;
      left: -27px;
      margin: 3px 0;
    }

    @include breakpoints.from(sm) {
      width: 16px;
      height: 16px;
      left: -39px;
      margin: 5px 0;
    }
  }

  section.professional-experience {
    .timeline {
      @include theme.apply using ($theme) {
        border-left: 2px solid map.get($theme, 'accent-color');
      }
      margin-left: 5px;

      &-item {
        position: relative;

        &::before {
          @include theme.apply using ($theme) {
            @include timeline-dot(
                url('@/assets/timeline-dot-stroke.svg'),
                map.get($theme, 'accent-color'),
            );
          }

        }

        &::after {
          @include theme.apply using ($theme) {
            @include timeline-dot(
                url('@/assets/timeline-dot-fill.svg'),
                map.get($theme, 'background-color'),
            );
          }
        }

        @include breakpoints.from(xs) {
          margin-left: 20px;
          margin-bottom: 26px;
        }

        @include breakpoints.from(sm) {
          margin-left: 30px;
          margin-bottom: 46px;
        }
      }
    }
  }

</style>
