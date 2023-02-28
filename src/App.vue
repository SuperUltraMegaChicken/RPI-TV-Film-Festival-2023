<template>
  <Suspense>
    <template #default>
      <v-app>
        <router-view></router-view>
      </v-app>
    </template>
    <template #fallback>loading...</template>
  </Suspense>
</template>

<script setup lang="ts">

import FirstView from "@/views/FirstView.vue";
</script>

<style scoped>

</style>