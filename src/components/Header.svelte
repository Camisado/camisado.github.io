<script>
  export let db;
</script>

<header>
  <div class="container">
    <section class="name">
      <div class="title">
        <span>{db.title}</span>
        <i class="icon icon-save"></i>
      </div>
      <div class="subtitle">{db.subtitle}</div>
    </section>
  </div>
</header>

<style lang="scss">
  @use 'sass:map';
  @use 'sass:color';
  @use '@/styles/theme';
  @use '@/styles/breakpoints';
  @use '@/styles/global';

  @include theme.apply using ($theme) {
    header {
      background-color: color.adjust(map.get($theme, 'accent-color'), $alpha: -0.98);
      color: map.get($theme, 'accent-color');

      section.name {
        .title {
          font-weight: 700;
          letter-spacing: 0.02em;

          .icon {
            opacity: 0.7;
            cursor: pointer;
          }

          .icon:hover {
            opacity: 1;
          }
        }

        .subtitle {
          font-weight: 400;
          text-transform: capitalize;
        }
      }

      @include breakpoints.from(xs) {
        margin-top: 36px;

        section.name {
          padding-top: 24px;
          padding-bottom: 24px;

          .title {
            font-size: 32px;
            line-height: 38px;
            margin-bottom: 6px;
          }

          .subtitle {
            font-size: 14px;
            line-height: 17px;
          }
        }
      }

      @include breakpoints.from(sm) {
        margin-top: 40px;

        section.name {
          padding-top: 40px;
          padding-bottom: 40px;

          .title {
            font-size: 52px;
            line-height: 62px;
            margin-bottom: 12px;
          }

          .subtitle {
            font-size: 22px;
            line-height: 26px;
          }
        }
      }
    }
  }

</style>
