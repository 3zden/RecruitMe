<script setup>
import { ref, defineProps} from "vue";
import jobsData from "@/assets/jobs.json";
import joblisting from "./joblisting.vue";



const jobs = ref(jobsData);
console.log(jobs.value[0]);


defineProps({
  limit: {
    type: Number,
    default: 100
  },  
  showButton: {
    type: Boolean,
  }

})



</script>

<template>
<!-- Browse Jobs -->
    <section class="bg-green-50 px-4 py-10">
      <div class="container-xl lg:container m-auto">
        <h2 class="text-3xl font-bold text-green-500 mb-6 text-center">
          Browse Jobs
        </h2>
        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
          <joblisting v-for="job in jobs.slice(0, limit)" :key="job.id" :job="job" />
        </div>
      </div>
    </section>

    <section v-if="showButton" class="m-auto max-w-lg my-10 px-6">
      <router-link
        to="/jobs"
        class="block bg-black text-white text-center py-4 px-6 rounded-xl hover:bg-gray-700"
        >View All Jobs</router-link
      >
    </section>
</template>