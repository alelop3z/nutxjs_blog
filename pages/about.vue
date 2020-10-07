<template>
  <div>Sobre miiiii</div>
</template>

<script>
export default {
  async asyncData ({ $content }) {
    const about = await $content('pages/about').fetch();

    return {
      about
    }
  }
}
</script>