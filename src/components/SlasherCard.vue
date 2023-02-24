<template>
  <div class="container">
    <v-card variant="tonal" class="card">
      <span>#{{index + 1}}</span>
      <v-avatar size="80" :image="picture"/>
      <span>{{firstName}} {{lastName}}</span>
      <span class="arrow">🔻</span>

    </v-card>
  </div>
</template>

<script setup lang="ts">
import NormanDates from "../assets/Norman_Dates.jpg";

defineProps({
  firstName: {
    type: String,
    required: true
  },
  lastName: {
    type: String,
    required: true
  },
  picture: {
    type: String,
    required: true
  },
  index: {
    type: Number,
    required: true
  }
})

</script>

<style scoped>
.container {
  margin-top: 5%;
  display: flex;
  justify-content: center;
}

.card {
  height: 100px;
  width: 300px;
  display: grid;
  align-items: center;
  color: white;
  grid-template-columns: 0.4fr 1.2fr 1.8fr 0.2fr;
  padding-left: 10px;
  padding-right: 10px;
}

.arrow {
  color: transparent;
  text-shadow: 0 0 0 #2fff00;
  transform: rotate(180deg);
}

</style>