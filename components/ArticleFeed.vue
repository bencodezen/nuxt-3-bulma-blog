<script setup>
const { data } = await useAsyncData('blogPosts', () => {
  return queryContent('/blog').find()
})
</script>

<template>
  <div class="container">
    <!-- START ARTICLE FEED -->
    <section class="articles">
      <div class="column is-8 is-offset-2">
        <!-- START ARTICLE -->
        <div
          v-for="blogPost in data"
          :key="blogPost.title"
          class="card article"
        >
          <div class="card-content">
            <div class="media">
              <div class="media-content has-text-centered">
                <p class="title article-title has-text-weight-bold">
                  <NuxtLink :to="blogPost._path">{{ blogPost.title }}</NuxtLink>
                </p>
                <div class="tags has-addons level-item are-medium">
                  <span class="tag is-rounded is-info">@skeetskeet</span>
                  <span class="tag is-rounded">May 10, 202X</span>
                </div>
              </div>
            </div>
            <div class="content article-body is-size-5">
              {{ blogPost.description }}
            </div>
          </div>
        </div>
        <!-- END ARTICLE -->
      </div>
    </section>
    <!-- END ARTICLE FEED -->
  </div>
</template>

<style>
.card-content {
  padding-top: 2.5rem;
  padding-bottom: 3rem;
}

.media-content .title {
  margin-bottom: 1rem;
}
</style>
