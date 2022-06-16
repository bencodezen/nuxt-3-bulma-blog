<script setup>
const { path } = useRoute()

const { data: blogPost } = await useAsyncData(`content-${path}`, () => {
  return queryContent().where({ _path: path }).findOne()
})
</script>

<template>
  <main>
    <TheHero>
      <template v-slot:default>{{ blogPost.title }}</template>

      <template v-slot:subtitle>
        <BlogPostMeta
          :author="blogPost.author"
          :date="blogPost['published-date']"
          color="dark"
        />
      </template>
    </TheHero>
    <div class="container">
      <section class="articles">
        <div class="column is-8 is-offset-2">
          <BlogPostCard :blogPost="blogPost">
            <ContentDoc />
          </BlogPostCard>
        </div>
      </section>
    </div>
  </main>
</template>

<style></style>
