<script setup>
import { ref, defineProps, onMounted} from "vue";
import joblisting from "./joblisting.vue";
import axios from "axios";





const jobs = ref([]);

onMounted(async () => {
  try {
    const response = await axios.get('http://localhost:5000/jobs');
    jobs.value = response.data;
  } catch (error) {
    console.error('Error fetching jobs:', error);
  }
})



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