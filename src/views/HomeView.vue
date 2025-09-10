<script setup>
import heroSec from "@/Components/heroSec.vue"
import HomeCards from "@/Components/HomeCards.vue";
import JobListings from "@/Components/JobListings.vue";

</script>

<template class = "bg-green-400">
  <heroSec title= "RecruitMe" subtitle="List your job to find the perfect developer for the role."/>
  <HomeCards/>
  <JobListings :limit="3" :showButton="true"/>
</template>

<style scoped>
body {
  background-image: '@/assets/Background.png';
}
</style>