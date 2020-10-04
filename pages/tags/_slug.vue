<template>
  <section class="latest-blog-section p-3 p-lg-5">
    <div class="container">
      <h2 class="section-title font-weight-bold mb-5">Últimos posts</h2>

      <div class="row">
        <div class="col-md-4 mb-5" v-for="(post, index) in posts" :key="index">
          <Post :post="post" />
        </div><!--//col-->
      </div><!--//row-->

      <div class="text-center py-3">
        <nuxt-link :to="'/tags/' + slug + '/2'" title="Ver más" class="btn btn-primary">
          Ver más posts
        </nuxt-link>
      </div>
    </div><!--//container-->
    
  </section>

</template>

<script>
export default {
  async asyncData({ $content, params, error }) {
    const slug = params.slug

    const posts = await $content("posts")
      .only(["title", "description", "publish_at", "tags", "image", "path"])
      .sortBy('publish_at', 'desc')
      .where({
        published: true,
        tags: { $contains: params.slug }
      })
      .fetch()
      .catch(err => {
        error({ statusCode: 404, message: "Página no encontrada" });
      });

    return {
      posts,
      slug
    }
  }
};
</script>