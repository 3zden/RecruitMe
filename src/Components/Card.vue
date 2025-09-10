<script setup>
import { defineProps } from "vue";

defineProps({
    bg: {
        type: String,
        default: 'bg-red-100',
    }
})
</script>


<template>
    <div :class="`${bg} p-6 rounded-3xl shadow-md`">
         
         <slot></slot>
         <slot name="button"></slot>
         
    </div>
</template>