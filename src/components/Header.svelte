<script>
  export let db;
</script>

<header>
  <div class="container">
    <section class="header">
      <div class="name">
        <div class="title">
          <span>{db.title}</span>
        </div>
        <div class="subtitle">{db.subtitle}</div>
      </div>

      <div class="logo">
        <i class="icon icon-badger"></i>
      </div>

    </section>
  </div>
</header>

<style lang="scss">
  @use 'sass:map';
  @use 'sass:color';
  @use '@/styles/theme';
  @use '@/styles/breakpoints';

  header {
    @include theme.apply using ($theme) {
      background-color: color.adjust(map.get($theme, 'accent-color'), $alpha: -0.98);
      color: map.get($theme, 'accent-color');
    }

    section.header {
      display: flex;
      justify-content: space-between;

      .name {
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

      .logo {
        align-self: center;
      }
    }

    @include breakpoints.from(xs) {
      margin-top: 36px;

      section.header {
        padding-top: 24px;
        padding-bottom: 24px;

        .name {
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

        .logo {
          .icon-badger {
            width: 60px;
            height: 60px;
          }
        }
      }
    }

    @include breakpoints.from(sm) {
      margin-top: 40px;

      section.header {
        padding-top: 40px;
        padding-bottom: 40px;

        .name {
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

        .logo {
          .icon-badger {
            width: 100px;
            height: 100px;
          }
        }
      }
    }
  }
</style>
