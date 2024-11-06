<template>
  <span></span>
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

span {
  align-self: center;
  justify-self: center;
  height: 160px;
  width: 160px;
  border: 7px solid var(--line-color);
  border-right: 7px solid transparent;
  border-radius: 50%;
  animation: spin 700ms ease-in-out 0ms infinite forwards;
}
</style>
