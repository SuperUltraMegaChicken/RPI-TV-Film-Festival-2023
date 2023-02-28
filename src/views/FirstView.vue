<template>
  <div>
    <v-btn :icon="true" class="scroll-up" @click="scrollTop">&#9650;</v-btn>
    <v-btn :icon="true" class="scroll-down" @click="scrollBottom">&#9660;</v-btn>
    <h1 class="title">Slasher Rankings</h1>
    <SlasherCard :reverse-arrow="1" :index="0" :picture="Jason" last-name="Voorhes jr" first-name="Jason" />
    <SlasherCard :reverse-arrow="1" :index="1" :picture="ConeHead" last-name="Head" first-name="Cone" />
    <SlasherCard :reverse-arrow="1" :index="2" :picture="Silencer" last-name="Silencer" first-name="The" />
    <SlasherCard :reverse-arrow="1" :index="3" :picture="NormanDates" last-name="Dates" first-name="Norman" />
    <div v-for="(person, index) in people.results" :key="person.email">
      <SlasherCard
        :index="index + 4" :picture="person.picture.large" :firstName="person.name.first" :lastName="person.name.last"
        :reverse-arrow="Math.floor(Math.random() * 2)"
      />
    </div>
    <SlasherCard :reverse-arrow="1" :index="300" :picture="RPITV" last-name="Subscribe" first-name="Please" />
    <SlasherCard :reverse-arrow="1" :index="301" :picture="NoUser" last-name="" first-name="User not found" />
  </div>
</template>

<script setup lang="ts">
import { nextTick } from "vue";
import SlasherCard from "@/components/SlasherCard.vue";
import { ref } from "vue";
import ConeHead from "@/assets/Conehead_2.png";
import Jason from "@/assets/Jason.jpeg";
import NormanDates from "@/assets/Norman_Dates.jpg";
import RPITV from "@/assets/rpitv_logo.png";
import Silencer from "@/assets/The_silencer.jpg";
import NoUser from "@/assets/User_not_found.webp";


const people = ref([]);

const res = await fetch("https://randomuser.me/api/?results=296");
const finalRes = await res.json();

people.value = finalRes;

const scrollBottom = () => {
  nextTick(() => {
    window.scrollTo({
      top: document.body.scrollHeight,
      left: 0,
      behavior: "smooth",
    });
  })
}
const scrollTop = () => {
  nextTick(() => {
    window.scrollTo({
      top: 0,
      left: 0,
      behavior: "smooth",
    })
  })
}
</script>

<style scoped>
div {
  background: rgb(2,0,36);
  background: linear-gradient(90deg, rgba(2,0,36,1) 0%, rgba(176,28,28,1) 71%, rgba(95,28,176,1) 100%);
}
.title {
  text-align: center;
  color: white;
  font-weight: lighter;
}
.scroll-down {
  position: fixed;
  top: 90%;
  left: 85%;
}
.scroll-up {
  position: fixed;
  top: 5%;
  left: 85%;
}
</style>