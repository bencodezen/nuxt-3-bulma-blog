<script setup>
defineProps({
  blogPost: Object,
  showMeta: {
    type: Boolean,
    default: false
  }
})
</script>

<template>
  <section :key="blogPost.title" class="blog-post-card card article">
    <div v-if="showMeta" class="media">
      <div class="media-content has-text-centered">
        <p class="title article-title has-text-weight-bold">
          <NuxtLink :to="blogPost._path">{{ blogPost.title }}</NuxtLink>
        </p>
        <BlogPostMeta
          :author="blogPost.author"
          :date="blogPost.dates.published"
        />
      </div>
    </div>
    <div class="card-content">
      <div class="content article-body is-size-5">
        <slot />
      </div>
    </div>
  </section>
</template>

<style scoped>
.blog-post-card {
  padding-top: 2.5rem;
  padding-bottom: 3rem;
}

.blog-post-card .card-content {
  padding: 1rem;
}

.blog-post-card .title {
  margin-bottom: 1rem;
}
</style>
