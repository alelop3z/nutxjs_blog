<template>
  <div class="blog-post-tags">
    <nuxt-link v-for="(tag, index) in tags" 
               :key="index"
               :to="'/tags/' + tag">
      {{ tag }}
    </nuxt-link>
  </div>
</template>

<script type="text/javascript">
  export default {
    props: ['tags']
  }
</script>