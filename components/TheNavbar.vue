<script setup>
const isMobileNavOpen = ref(false)
</script>

<template>
  <nav class="navbar">
    <div class="container">
      <div class="navbar-brand">
        <nuxt-link to="/" class="navbar-item has-text-weight-bold is-size-5">
          Nuxt Content v2 + Bulma Blog
        </nuxt-link>
        <span
          class="navbar-burger burger"
          data-target="navbarMenu"
          @click="isMobileNavOpen = !isMobileNavOpen"
        >
          <span></span>
          <span></span>
          <span></span>
        </span>
      </div>
      <div
        id="navbarMenu"
        class="navbar-menu"
        :class="isMobileNavOpen ? 'is-active' : ''"
      >
        <div class="navbar-end">
          <a class="navbar-item is-active"> Home </a>
          <a class="navbar-item"> Blog </a>
        </div>
      </div>
    </div>
  </nav>
</template>

<style></style>
