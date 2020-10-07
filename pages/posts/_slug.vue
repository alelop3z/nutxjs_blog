<template>
  <article class="blog-post px-3 py-5 p-md-5">
    <div class="container single-col-max-width">
      <header class="blog-post-header">
        <h1 class="title mb-2">{{ post.title }}</h1>
        <div class="meta mb-3"><span class="date">Published 2 days ago</span><span class="time">5 min read</span><span class="comment"><a href="#">4 comments</a></span></div>
      </header>
      
      <div class="blog-post-body">
        <nuxt-content :document="post" class="leading-loose" />
        <div v-if="prev">PREV: {{ prev.title }}</div>
        <div v-if="next">NEXT: {{ next.title }}</div>
      </div>
    </div>
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    const post = await $content(`posts/${params.slug}`)
      .fetch()
      .catch(err => {
        error({ statusCode: 404, message: "Página no encontrada" });
      });

    const [prev, next] = await $content('posts')
      .only(['title', 'slug'])
      .sortBy('createdAt', 'asc')
      .surround(params.slug)
      .fetch()

    return {
      next,
      post,
      prev 
    };
  }
};
</script>