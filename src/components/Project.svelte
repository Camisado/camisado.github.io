<script>
  export let db;
  import dictionary from '@/data/dictionary.json';

  const readMoreId = Math.random();
</script>

<div class="project">
  <input class="read-more-state" type="checkbox" id={readMoreId}>
  <div class="read-more-wrap">
    <div class="name">
      <span class="label label-colon">{dictionary.project.label}</span>
      <span class="value">{db.name}</span>
    </div>
    <div class="description">
      {db.description}
    </div>
    <div class="responsibilities read-more-target">
      <span class="label label-colon">{dictionary.project.responsibilities}</span>
      <ul>
        {#each db.responsibilities as responsibility}
          <li>{responsibility}</li>
        {/each}
      </ul>
    </div>
    <div class="technologies read-more-target">
      <span class="label label-colon">{dictionary.project.technologies}</span>
      <span class="value">{db.technologies.join(', ')}</span>
    </div>
  </div>
  <label class="read-more-trigger"
         for={readMoreId}
         data-show-more-label={dictionary.project.showMore}
         data-show-less-label={dictionary.project.showLess}></label>
</div>

<style lang="scss">
  @use 'sass:map';
  @use '@/styles/theme';
  @use '@/styles/breakpoints';

  @include theme.apply using($theme) {
    div.project {
      .responsibilities > ul {
        margin: 0;
        padding-left: 20px;
      }

      .read-more-state {
        display: none;
      }

      .read-more-target {
        display: none;

        //opacity: 0;
        //visibility: hidden;
        //max-height: 0;
        //font-size: 0;
        //line-height: 0;
        //transition: 0.25s ease;
      }

      .read-more-state:checked ~ .read-more-wrap .read-more-target {
        display: inherit;

        //opacity: 1;
        //visibility: visible;
        //font-size: inherit;
        //line-height: inherit;
        //max-height: 999em;
      }

      .read-more-state ~ .read-more-trigger::before {
        content: attr(data-show-more-label);
      }

      .read-more-state:checked ~ .read-more-trigger::before {
        content: attr(data-show-less-label);
      }

      .read-more-trigger {
        cursor: pointer;
        color: map.get($theme, 'accent-color');
      }

      @include breakpoints.from(xs) {
        .name,
        .description,
        .responsibilities,
        .technologies {
          margin-bottom: 8px;
        }
      }

      @include breakpoints.from(sm) {
        .name,
        .description,
        .responsibilities,
        .technologies {
          margin-bottom: 10px;
        }
      }
    }
  }
</style>
