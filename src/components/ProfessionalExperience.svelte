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
  @use '@/styles/icons';
  @use '@/styles/breakpoints';


  @mixin timeline-dot($src, $color) {
    content: '';
    @include icons.masked-svg($src, $color,);
    position: absolute;
    top: 0;

    @include breakpoints.from(xs) {
      width: 10px;
      height: 10px;
      left: -26px;
      margin: 4px 0;
    }

    @include breakpoints.from(sm) {
      width: 12px;
      height: 12px;
      left: -37px;
      margin: 7px 0;
    }
  }

  @include theme.apply using ($theme) {
    section.professional-experience {
      .timeline {
        border-left: 2px solid map.get($theme, 'accent-color');
        margin-left: 5px;

        &-item {
          position: relative;

          &::before {
            @include timeline-dot(
                url('@/assets/timeline-dot-stroke.svg'),
                map.get($theme, 'accent-color'),
            );
          }

          &::after {
            @include timeline-dot(
                url('@/assets/timeline-dot-fill.svg'),
                map.get($theme, 'background-color'),
            );
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
  }

</style>
