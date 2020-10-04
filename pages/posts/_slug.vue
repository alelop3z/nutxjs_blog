<template>
  <div>
    <h1 class="my-8 max-w-full m-auto text-3xl text-center font-medium">{{ post.title }}</h1>
    <h3 class="py-4 text-center uppercase">{{ post.description }}</h3>
    <nuxt-content :document="post" class="leading-loose" />
    
    <div v-if="prev">PREV: {{ prev.title }}</div>
    <div v-if="next">NEXT: {{ next.title }}</div>
  </div>
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