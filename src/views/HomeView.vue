<script setup>
import heroSec from "@/Components/heroSec.vue"
import HomeCards from "@/Components/HomeCards.vue";
import JobListings from "@/Components/JobListings.vue";

</script>

<template>
  <heroSec title= "RecruitMe" subtitle="List your job to find the perfect developer for the role."/>
  <HomeCards/>
  <JobListings :limit="3" :showButton="true"/>
</template>