<script setup>
import whiteLogo from '../assets/whiteLogo.png';
import { defineProps } from "vue";
import { RouterLink,useRoute } from "vue-router";

defineProps({
    title: {
        type: String,
        default: 'RecruitMe'  

    }
});

const isActive = (routePath) => {
  const route = useRoute();
  return (routePath === route.path );


}

</script>

<template>
<nav class="">
      <div class="mx-auto max-w-7xl px-2 sm:px-6 lg:px-8">
        <div class="flex h-20 items-center justify-between">
          <div
            class="flex flex-1 items-center justify-center md:items-stretch md:justify-start"
          >
            <!-- Logo -->
            <RouterLink class="flex flex-shrink-0 items-center mr-4" to="/">
              <img class="h-10 w-auto " :src="whiteLogo" alt="RecruitMe Logo" />
              <span class="hidden md:block text-white text-2xl font-bold ml-2"
                >{{ title  }}</span
              >
            </RouterLink>
            <div class="md:ml-auto">
              <div class="flex space-x-2">
                <router-link
                  to="/"
                  :class="[isActive('/') ? 'bg-[#b8c296]/10 hover:bg-[#b8c296]/20' : ' hover:bg-[#b8c296]/20' , 'text-white', 'hover:text-white', 'rounded-3xl', 'px-3', 'py-2']" 
                  >Home</router-link
                >
                <router-link to='/jobs'
                  :class="[isActive('/jobs') ? 'bg-[#b8c296]/10 hover:bg-[#b8c296]/20' :  'hover:bg-[#b8c296]/20' , 'text-white', 'hover:text-white', 'rounded-3xl', 'px-3', 'py-2']"
                  >Jobs</router-link
                >
                <router-link
                  to="/add-jobs"
                  :class="[isActive('/add-jobs') ? 'bg-[#b8c296]/10 hover:bg-[#b8c296]/20' : ' hover:bg-[#b8c296]/20' , 'text-white', 'hover:text-white', 'rounded-3xl', 'px-3', 'py-2']"
                  >Add Job</router-link
                >
              </div>
            </div>
          </div>
        </div>
      </div>
    </nav>
</template>

<style scoped>
background-color: red;
/* Add this to your <style scoped> */
.white-logo {
  filter: brightness(0) invert(1);
}
   
</style>