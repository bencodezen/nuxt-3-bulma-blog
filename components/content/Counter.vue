<script setup>
const count = ref(0)

const addCount = () => {
  count.value++
}
</script>

<template>
  <div>
    <p>{{ count }}</p>
    <button @click="addCount">Add Count</button>
  </div>
</template>

<style></style>
