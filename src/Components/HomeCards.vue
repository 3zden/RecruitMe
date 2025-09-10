<script setup>
import Card from "./Card.vue"
import {RouterLink} from "vue-router"


</script>

<template>
    <section class="py-4">
      <div class="container-xl lg:container m-auto">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4 p-4 rounded-lg">
          <Card bg="bg-[#AAB299]">
            <template #button>            
              <RouterLink
              to="/jobs"
              class="inline-block bg-[#2B3A1F] text-white rounded-lg px-4 py-2 hover:bg-[#2B3A1F]/80"
              >
              Browse Jobs
            </RouterLink>
            </template>
            <h2 class="text-[#2B3A1F] text-2xl font-bold">For Developers</h2>
            <p class="text-[#2B3A1F] mt-2 mb-4">
              Browse our Vue jobs and start your career today
            </p>

          </Card>
          <Card bg= "bg-[#788F5D]">
            <h2 class="text-[#1B1E17] text-2xl font-bold">For Employers</h2>
            <p class="text-[#1B1E17] mt-2 mb-4">
              List your job to find the perfect developer for the role
            </p>
            <RouterLink
              to="/add-jobs"
              class="inline-block bg-[#1B1E17] text-white rounded-lg px-4 py-2 hover:bg-[#1B1E17]/80"
            >
              Add Job
          </RouterLink>
          </Card>
        </div>
      </div>
    </section>
</template>