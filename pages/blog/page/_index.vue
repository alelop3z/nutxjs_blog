<template>
  <div>
    <section class="latest-blog-section p-3 p-lg-5">
			<div class="container">
				<h2 class="section-title font-weight-bold mb-5">Posts</h2>

				<div class="row">
					<div class="col-md-4 mb-5" v-for="(post, index) in posts" :key="index">
            <Post :post="post" />
					</div>
				</div>
      </div>
		</section>
  </div>
</template>

<script>
export default {
  async asyncData ({ $content, params }) {
    let limit = 12

    const posts = await $content("posts")
      .only(["title", "description", "publish_at", "tags", "image", "path"])
      .sortBy('publish_at', 'desc')
      .limit(limit)
      .skip((params.index - 1) * limit)
      .where({
        published: true
      })
      .fetch()
      .catch(err => {
        error({ statusCode: 404, message: "Página no encontrada" });
      });

    return {
      posts
    }
  }
}
</script>