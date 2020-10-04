<template>
  <ul class="blog-tags">
    <li v-for="(tag, index) in tags" :key="index">
      <nuxt-link :to="'/tags/' + tag">{{ tag }}</nuxt-link>
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      tags: []
    }
  },
  mounted() {
    this.$axios.$get("/_content/posts?only=tags")
        .then((response) => {
          let tags = [] 
          for(let i = 0; i < response.length; i++) {
            tags.push(response[i].tags)
          }
          
          this.tags = [...new Set(tags.flat(1))]
        })
  }
}
</script>