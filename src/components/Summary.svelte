<script>
  import dictionary from '@/data/dictionary.json';

  export let db;
</script>

<section class="summary">
  <div class="title">{dictionary.summary}</div>
  <ul>
    {#each db as item}
      <li>{item}</li>
    {/each}
  </ul>
</section>

<style lang="scss">
  @use "sass:map";
  @use '@/styles/theme';
  @use '@/styles/breakpoints';

  @include theme.apply() using ($theme) {
    section.summary {
      ul {
        padding-left: 20px;
        list-style: none;

        li {
          &::before {
            content: "\2022";
            color: map.get($theme, 'accent-color');
            font-weight: 800;
            display: inline-block;
            width: 18px;
            margin-left: -18px;
            line-height: 18px;
          }

          @include breakpoints.from(xs) {
            margin-bottom: 14px;

            &::before {
              font-size: 18px;
            }
          }

          @include breakpoints.from(sm) {
            margin-bottom: 20px;

            &::before {
              font-size: 25px;
            }
          }
        }

      }
    }
  }
</style>
