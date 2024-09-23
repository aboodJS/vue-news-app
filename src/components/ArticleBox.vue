<script setup>
defineProps(['title', 'desc', 'link'])
</script>

<template>
  <h2>{{ title }}</h2>
  <p>{{ desc }}</p>
  <button>
    <a :href="link" target="_blank">read the article</a>
  </button>
</template>

<style scoped>
a {
  text-decoration: none;
  color: black;
}

button {
  border-radius: var(--br-radius);
  border: none;
  background-color: var(--line-color);
}
</style>
