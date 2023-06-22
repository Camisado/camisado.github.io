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
      {#each db.description as paragraph }
        <p>{paragraph}</p>
      {/each}
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

  div.project {
    .responsibilities > ul {
      margin: 0;
      padding-left: 20px;
    }

    .description {
      p {
        margin: 0 0 4px 0;
      }
    }

    .read-more-state {
      display: none;
    }

    .read-more-target {
      display: none;
    }

    .read-more-state:checked ~ .read-more-wrap .read-more-target {
      display: inherit;
    }

    .read-more-state ~ .read-more-trigger::before {
      content: attr(data-show-more-label);
    }

    .read-more-state:checked ~ .read-more-trigger::before {
      content: attr(data-show-less-label);
    }

    .read-more-trigger {
      cursor: pointer;
      @include theme.apply using($theme) {
        color: map.get($theme, 'accent-color');
      }
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

    @media print {
      .read-more-target {
        display: block;
      }

      .read-more-trigger {
        display: none;
      }

      .read-more-wrap {
        div {
          break-inside: avoid;
          page-break-inside: avoid;
        }
      }
    }
  }
</style>
