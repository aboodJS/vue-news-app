<template>
  <div></div>
</template>

<style scoped>
@keyframes spin {
  from {
    transform: rotate(0deg);
  }

  to {
    transform: rotate(360deg);
  }
}

div {
  height: 120px;
  width: 120px;
  border: 5px solid var(--line-color);
  border-right: 5px solid transparent;
  border-radius: 50%;
  animation: spin 700ms ease-in-out 0ms infinite forwards;
}
</style>
