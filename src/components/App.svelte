<script>
  import Header from '@/components/Header.svelte';
  import Main from '@/components/Main.svelte';
  import db from '@/data/db.json'
</script>
<div class="app">
  <Header db={db.header} />
  <Main db={db.main} />
</div>

<style global lang="scss">
  @use 'sass:map';
  @use 'sass:color';
  @use '@/styles/theme';
  @use '@/styles/breakpoints';

  .app {
    font-family: 'Barlow', sans-serif;
    font-style: normal;
    font-weight: 300;
    overflow: auto;

    @include theme.apply using($theme) {
      background: map.get($theme, 'background-color');
      color: map.get($theme, 'text-color');
    }

    @include breakpoints.from(xs) {
      font-size: 14px;
      line-height: 19px;
    }

    @include breakpoints.from(sm) {
      font-size: 18px;
      line-height: 25px;
    }

    :global(::selection) {
      @include theme.apply using($theme) {
        background-color: color.adjust(map.get($theme, 'accent-color'), $alpha: -0.9);
      }
    }
  }
</style>
