<script>
  import Header from '@/components/Header.svelte';
  import Main from '@/components/Main.svelte';
  import db from '@/data/db.json'
</script>

<Header db={db.header} />
<Main db={db.main} />

<style lang="scss">
  //@use "sass:map";
  //@use '@/styles/theme';
  //@use '@/styles/breakpoints';
  //
  //@include theme.apply using($theme) {
  //}
</style>
