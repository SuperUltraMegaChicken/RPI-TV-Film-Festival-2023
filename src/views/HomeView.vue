<template>
  <div>
    <h1 class="title">Slasher Rankings</h1>
    <div v-for="(person, index) in people.results" :key="person.email">
      <SlasherCard :index="index" :picture="person.picture.thumbnail" :firstName="person.name.first" :lastName="person.name.last" />
    </div>
  </div>
</template>

<script setup lang="ts">

import SlasherCard from "@/components/SlasherCard.vue";
import { ref } from "vue";

const people = ref([]);

const res = await fetch("https://randomuser.me/api/?results=300");
const finalRes = await res.json();

people.value = finalRes;

console.log(people.value);
</script>

<style scoped>

.title {
  text-align: center;
  color: white;
  font-weight: lighter;
}
</style>