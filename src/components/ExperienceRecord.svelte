<script>
  export let db;
  import dictionary from '@/data/dictionary.json';
  import Project from '@/components/Project.svelte';

  const businessTripType = 'business-trip';
</script>

<article class="experience-record">
  <div class="company">
    <div class="name">
      {#if db.company.type === businessTripType}
        <span class="from">{db.company.from}</span>
        <i class="icon icon-plane"></i>
        <span class="to">{db.company.to}</span>
      {:else}
        {db.company.name}
      {/if}
    </div>

    <div class="duration">{db.company.workDuration}</div>
  </div>

  <div class="position">
    <span class="label label-colon">{dictionary.experienceRecord.position}</span>
    <span class="value">{db.position}</span>
  </div>

  {#each db.projects as project, index}
    <Project db={project} />

    {#if index !== db.projects.length - 1}
      <div class="delimiter">
        <div class="delimiter-line"></div>
        <i class="icon icon-scissors"></i>
      </div>
    {/if}
  {/each}

</article>

<style lang="scss">
  @use 'sass:map';
  @use '@/styles/breakpoints';
  @use '@/styles/theme';
  @use '@/styles/global';

  @include theme.apply using ($theme) {
    article.experience-record {
      .company {
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        align-items: baseline;

        .name {
          color: map.get($theme, 'accent-color');
          font-weight: 500;
        }

        .duration {
          color: map.get($theme, 'accent-color');
          font-weight: 400;
        }
      }

      div.delimiter {
        display: flex;
        align-items: center;

        div.delimiter-line {
          overflow: hidden;
          position: relative;
          height: 1px;
          width: 100%;
        }

        div.delimiter-line::before {
          opacity: 0.7;
          content: '';
          position: absolute;
          border: 5px dashed map.get($theme, 'accent-color');
          top: 0;
          bottom: 0;
          left: 0;
          right: 0;
        }
      }

      @include breakpoints.from(xs) {
        .company {
          margin-bottom: 12px;

          .name {
            font-size: 16px;
            line-height: 19px;
          }

          .duration {
            font-size: 12px;
            line-height: 14px;
          }
        }

        .position {
          margin-bottom: 10px;
        }

        .delimiter {
          margin-top: 10px;
          margin-bottom: 10px;
        }

        .icon {
          width: 16px;
          height: 16px;

          &-plane {
            margin: 0 8px;
          }
        }
      }

      @include breakpoints.from(sm) {
        .company {
          margin-bottom: 16px;

          .name {
            font-size: 22px;
            line-height: 26px;
          }

          .duration {
            font-size: 18px;
            line-height: 25px;
          }
        }

        .position {
          margin-bottom: 14px;
        }

        .delimiter {
          margin-top: 14px;
          margin-bottom: 14px;
        }

        .icon {
          width: 20px;
          height: 20px;

          &-plane {
            margin: 0 16px;
          }
        }
      }
    }
  }
</style>
