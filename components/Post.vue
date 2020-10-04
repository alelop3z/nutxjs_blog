<template>
  <div class="card blog-post-card">
    <nuxt-link :to="post.path" class="theme-link" v-if="post.image">
      <img class="card-img-top" :src="post.image" :alt="post.title">
    </nuxt-link>
    
    <div class="card-body">
      <h5 class="card-title">
        <nuxt-link :to="post.path" class="theme-link">{{ post.title }}</nuxt-link>
      </h5>
      <p class="card-text">{{ post.description }}</p>
      <p class="mb-0">
        <nuxt-link :to="post.path" class="theme-link">Leer más →</nuxt-link>
      </p>
      
      <PostTags :tags="post.tags" />
    </div>

    <div class="card-footer">
      <small class="text-muted">{{ post.publish_at }}</small>
    </div>
  </div><!--//card-->
</template>

<script type="text/javascript">
  export default {
    props: ['post']
  }
</script>