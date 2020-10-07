<template>
  <div>
    <div class="about-me-section p-3 p-lg-5">
      <div class="container">
        <div class="profile-teaser media flex-column flex-lg-row">
          <div class="media-body">
            <h2 class="name font-weight-bold mb-1">{{ index.title }}</h2>
            <div class="tagline mb-3">{{ index.subtitle }}</div>
            <div class="bio mb-4">
              <nuxt-content :document="index" />
            </div><!--//bio-->

            <div class="mb-4">
              <nuxt-link class="btn btn-secondary mb-3" to="/cv" title="Mi CV">
                <span class="d-none d-md-inline">Ver </span> CV
              </nuxt-link>
            </div>
          </div><!--//media-body-->

          <img class="profile-image mb-3 mb-lg-0 ml-lg-5 mr-md-0" src="assets/images/profile-lg.jpg" alt="">
        </div>
      </div>
    </div>

    <section class="latest-blog-section p-3 p-lg-5">
			<div class="container">
				<h2 class="section-title font-weight-bold mb-5">Últimos posts</h2>

				<div class="row">
					<div class="col-md-4 mb-5" v-for="(post, index) in posts" :key="index">
            <Post :post="post" />
					</div>
				</div>

				<div class="text-center py-3">
          <nuxt-link to="/blog" title="Ver blog" class="btn btn-primary">
            Ver más posts
          </nuxt-link>
        </div>
			</div>
		</section>
  </div>
</template>

<script>
export default {
  async asyncData ({ $content }) {
    const index = await $content('pages/index').fetch();

    const posts = await $content("posts")
      .only(["title", "description", "publish_at", "tags", "image", "path"])
      .limit(6)
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