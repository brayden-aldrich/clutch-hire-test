<template>
  <router-view />
</template>

<style lang="scss">
html,
body,
#app {
  min-height: 100dvh;
  background-color: #fff;
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.25s;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
