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
  align-self: center;
  border-radius: var(--br-radius);
  border: none;
  background-color: var(--line-color);
}

@media (max-width: 700px) {
  p {
    display: none;
  }

  h2 {
    font-size: 125%;
  }

  button {
    border-radius: 4px;
    height: 40px;
  }
}
</style>
