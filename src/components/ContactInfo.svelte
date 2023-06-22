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
      case 'save':
      case 'email': return {};
    }
  }

  const onClickHandler = (linkName) => {
    switch (linkName) {
      case 'save': return onSave();
      case 'linkedIn':
      case 'facebook':
      case 'email': return null;
    }
  }

  const onSave = () => {
    console.log('onsave');
    window.print();
  }
</script>

<section class="contact-info">
  <div class="title">{dictionary.contactInfo}</div>

  {#each db as link}
    <div class="contact">
      <i class="icon icon-{link.name}"></i>
      <div class="link">
        <a href={link.href} {...extraLinkAttrs(link.name)} on:click={() => onClickHandler(link.name)}>{link.label}</a>
      </div>
    </div>
  {/each}
</section>

<style lang="scss">
  @use '@/styles/breakpoints';

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

    @media print {
      display: none;
    }
  }
</style>
