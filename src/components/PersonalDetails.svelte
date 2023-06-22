<script>
  import Summary from '@/components/Summary.svelte';

  export let db;
  import ContactInfo from '@/components/ContactInfo.svelte';
  import TechnicalSkills from '@/components/TechnicalSkills.svelte';
  import Education from '@/components/Education.svelte';
</script>

<section class="personal-details">
  <ContactInfo db={db.contactInfo} />
  <Summary db={db.summary} />
  <TechnicalSkills db={db.techSkills} />
  <Education db={db.education} />
</section>

<style lang="scss">
  @use '@/styles/breakpoints';

  section.personal-details {
    @include breakpoints.from(xs) {
      :global(section) {
        margin-bottom: 36px;
      }
    }

    @include breakpoints.from(sm) {
      :global(section) {
        margin-bottom: 50px;
      }
    }

    @media print {
      page-break-after: always;
      break-after: page;
    }
  }
</style>
