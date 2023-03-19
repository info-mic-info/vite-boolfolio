<script>
import AppHeader from "./components/AppHeader.vue";

export default {
  components: {
    AppHeader,
  },
};
</script>

<template>
  <AppHeader></AppHeader>
  <router-view></router-view>
  <PostMain />
</template>

<style scoped>
</style>
