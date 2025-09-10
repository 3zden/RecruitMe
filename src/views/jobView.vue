<script setup>
import { RouterLink, useRoute } from 'vue-router'
import { onMounted } from 'vue'
import axios from 'axios'
import { reactive, ref } from 'vue'
import NotFoundView from './NotFoundView.vue'

const route = useRoute()
const jobId = route.params.id

const state = reactive({ job: {}, isLoading: true })

onMounted(async () => {
  try {
    const response = await axios.get(`http://localhost:5000/jobs/${jobId}`)
    console.log(response.data)
    state.job = response.data

  } catch (error) {
    console.error('Error fetching jobs:', error)
  }
  finally {
    state.isLoading = false
  }
})
</script>

<template>
  <section>
    <div class="container m-auto py-6 px-6">
      <router-link to="/jobs" class="text-white hover:text-[#FCFFEC] flex items-center">
        <i class="fas fa-arrow-left mr-2"></i> Back to Job Listings
      </router-link>
    </div>
  </section>
  <section v-if="!state.isLoading">
    <div class="container m-auto py-10 px-6">
      <div class="grid grid-cols-1 md:grid-cols-70/30 w-full gap-6">
        <main>
          <div class="bg-white p-6 rounded-l-3xl rounded-r-md shadow-md text-center md:text-left">
            <div class="text-gray-500 mb-4">{{ state.job.type }}</div>
            <h1 class="text-3xl font-bold mb-4">{{ state.job.title }}</h1>
            <div class="text-gray-500 mb-4 flex align-middle justify-center md:justify-start">
              <i class="fa-solid fa-location-dot text-lg text-orange-700 mr-2"></i>
              <p class="text-orange-700">{{ state.job.location }}</p>
            </div>
          </div>

          <div class="bg-white p-6 rounded-3xl rounded-r-md shadow-md mt-6">
            <h3 class="text-green-800 text-lg font-bold mb-6">Job Description</h3>

            <p class="mb-4">
              {{ state.job.description }}
            </p>

            <h3 class="text-green-800 text-lg font-bold mb-2">Salary</h3>

            <p class="mb-4">{{ state.job.salary }}</p>
          </div>
        </main>

        <!-- Sidebar -->
        <aside>
          <!-- Company Info -->
          <div class="bg-white p-6 rounded-3xl rounded-l-md shadow-md">
            <h3 class="text-xl font-bold mb-6">Company Info</h3>

            <h2 class="text-2xl">{{ state.job.company.name }}</h2>

            <p class="my-2">
              {{ state.job.company.description }}
            </p>

            <hr class="my-4" />

            <h3 class="text-xl">Contact Email:</h3>

            <p class="my-2 bg-green-100 p-2 font-bold">
              {{ state.job.company.contactEmail }}
            </p>

            <h3 class="text-xl">Contact Phone:</h3>

            <p class="my-2 bg-green-100 p-2 font-bold">{{ state.job.company.contactPhone }}</p>
          </div>

          <!-- Manage -->
          <div class="bg-white p-6 rounded-3xl rounded-tl-md shadow-md mt-6">
            <h3 class="text-xl font-bold mb-6">Manage Job</h3>
            <a
              href="add-job.html"
              class="bg-[#788F5D] hover:bg-[#6B7A4D] text-white text-center font-bold py-2 px-4 rounded-full w-full focus:outline-none focus:shadow-outline mt-4 block"
              >Edit Job</a
            >
            <button
              class="bg-[#5B2333] hover:bg-[#4A1F26] text-white font-bold py-2 px-4 rounded-full w-full focus:outline-none focus:shadow-outline mt-4 block"
            >
              Delete Job
            </button>
          </div>
        </aside>
      </div>
    </div>
  </section>
  <section v-else>
    <NotFoundView />
  </section>
</template>
