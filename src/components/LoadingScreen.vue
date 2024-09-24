<template>
  <i></i>
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
item {
  animation-name: spin;
  animation-duration: 1.2s;
  animation-timing-function: linear;
  animation-iteration-count: infinite;
  justify-self: center;
  align-self: center;
  height: 120px;
  width: 120px;
  border: 4px solid var(--line-color);
  border-left: 4px solid transparent;
  border-radius: 50%;
}
</style>
