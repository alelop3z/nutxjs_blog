<template>
  <div>
    <Header />
    
    <div class="main-wrapper">
      <Nuxt />
      <Footer />
    </div><!--//main-wrapper-->
  </div>
</template>

<script>
export default {
  head: {
    bodyAttrs: {
      class: 'dark-mode'
    }
  }
}
</script>