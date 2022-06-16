<script setup>
defineProps({
  blogPost: Object
})
</script>

<template>
  <section :key="blogPost.title" class="card article">
    <div class="card-content">
      <div class="content article-body is-size-5">
        <slot />
      </div>
    </div>
  </section>
</template>
