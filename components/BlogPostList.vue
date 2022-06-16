<script setup>
const { data: blogPostList } = await useAsyncData('blogPosts', () => {
  return queryContent('/blog').find()
})
</script>

<template>
  <div class="container">
    <section class="articles">
      <div class="column is-8 is-offset-2">
        <div
          v-for="blogPost in blogPostList"
          :key="blogPost.title"
          class="card article"
        >
          <NuxtLink :to="blogPost._path">
            <BlogPostCard :blogPost="blogPost" :showMeta="true">
              {{ blogPost.description }}
            </BlogPostCard>
          </NuxtLink>
        </div>
      </div>
    </section>
  </div>
</template>

<style></style>
