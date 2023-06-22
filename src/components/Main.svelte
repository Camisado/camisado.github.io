<script>
  export let db;
  import PersonalDetails from '@/components/PersonalDetails.svelte';
  import ProfessionalExperience from '@/components/ProfessionalExperience.svelte';
</script>

<main>
  <div class="container">
    <div class="content">
      <div class="content__left-column">
        <PersonalDetails db={db.personalDetails} />
      </div>

      <div class="content__right-column">
        <ProfessionalExperience db={db.experience} />
      </div>
    </div>
  </div>
</main>

<style lang="scss">
  @use '@/styles/breakpoints';

  div.content {
    display: flex;
    flex-wrap: wrap;

    @include breakpoints.from(xs) {
      padding-top: 36px;
      padding-bottom: 0;
    }

    @include breakpoints.from(sm) {
      padding-top: 60px;
      padding-bottom: 0;
    }

    @include breakpoints.from(md) {
      &__left-column {
        flex: 4;
      }

      &__right-column {
        flex: 8;
        margin-left: 30px;
      }
    }

    @media print {
      display: block;
      padding-top: 0;

      &__right-column {
        flex: 8;
        margin-left: 0;
      }
    }
  }
</style>
