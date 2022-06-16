<script setup>
const { path } = useRoute()

const { data: blogPost } = await useAsyncData(`content-${path}`, () => {
  return queryContent().where({ _path: path }).findOne()
})

const publishedDate = computed(() => {
  return new Date(blogPost.value['published-date']).toDateString()
})
</script>

<template>
  <main>
    <TheHero>
      <template v-slot:default>{{ blogPost.title }}</template>

      <template v-slot:subtitle>
        <div class="media">
          <div class="media-content has-text-centered">
            <div class="tags has-addons level-item are-medium">
              <span class="tag is-rounded is-dark">{{ blogPost.author }}</span>
              <span class="tag is-rounded">{{ publishedDate }}</span>
            </div>
          </div>
        </div>
      </template>
    </TheHero>
    <div class="container">
      <section class="articles">
        <div class="column is-8 is-offset-2">
          <BlogPostCard :blogPost="{ title: 'test' }">
            <ContentDoc />
          </BlogPostCard>
        </div>
      </section>
    </div>
  </main>
</template>

<style></style>
