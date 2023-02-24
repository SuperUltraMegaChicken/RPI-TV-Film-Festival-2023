<template>
  <Suspense>
    <template #default>
      <HomeView />
    </template>
    <template #fallback>loading...</template>
  </Suspense>
</template>

<script setup lang="ts">

import HomeView from "@/views/HomeView.vue";
</script>

<style scoped>

</style>