<template>
  <div>
    <h1 class="text-3xl py-6">{{ index.title }}</h1>
    <p class="text-xl py-3">{{ index.description }}</p>

    <ul class="list-disc list-inside mb-4">
      <li v-for="(post, index) in posts" :key="index">
        TITLE: {{ post.title }}
        <img :src="post.image" style="max-width: 200px;" />
        PUBLISH_AT: {{ new Date(post.publish_at).toLocaleDateString() }}
        <nuxt-link :to="post.path" class="underline">{{ post.title }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  layout: 'default',
  async asyncData ({ $content }) {
    const index = await $content('pages/index').fetch();

    const posts = await $content("posts")
      .only(["title", "description", "publish_at", "image", "path"])
      .limit(5)
      .sortBy('publish_at', 'desc')
      .where({
        published: true
      })
      .fetch()
      .catch(err => {
        error({ statusCode: 404, message: "Página no encontrada" });
      });

    return {
      index, 
      posts
    }
  }
}
</script>