<script>
  import dictionary from '@/data/dictionary.json';

  export let db;

  const extraLinkAttrs = (linkName) => {
    switch (linkName) {
      case 'linkedIn':
      case 'facebook': return {
        target: '_blank',
        rel: 'noopener',
      };
      case 'email': return {};
    }
  }
</script>

<section class="contact-info">
  <div class="title">{dictionary.contactInfo}</div>
  {#each db as link}
    <div class="contact">
      <i class="icon icon-{link.name}"></i>
      <div class="text">
        <a href={link.href} {...extraLinkAttrs(link.name)}>{link.label}</a>
      </div>
    </div>
  {/each}
</section>

<style lang="scss">
  @use 'sass:map';
  @use '@/styles/theme';
  @use '@/styles/breakpoints';
  @use '@/styles/global';

  @include theme.apply using ($theme) {
    section.contact-info {
      display: flex;
      flex-direction: column;
      align-items: flex-start;

      .contact {
        display: flex;
        align-items: center;
      }

      @include breakpoints.from(xs) {
        .contact {
          &:not(:last-child) {
            margin-bottom: 14px;
          }

          .icon {
            margin-right: 14px;
          }
        }
      }

      @include breakpoints.from(sm) {
        .contact {
          &:not(:last-child) {
            margin-bottom: 18px;
          }

          .icon {
            margin-right: 16px;
          }
        }
      }
    }
  }
</style>
