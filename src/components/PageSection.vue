<script setup>
defineProps({
  title: String,
  content: String,
  imageUrl: String,
  bgColor: String,
});
</script>

<template>
  <div class="container mx-auto py-8 px-4" :class="bgColor">
    <h2 class="text-2xl font-semibold text-center">{{ title }}</h2>
    <p>{{ content }}</p>
    <div class="mt-4" v-if="imageUrl">
      <img :src="imageUrl" alt="Image" class="rounded-lg w-full sm:w-3/4 md:w-2/3 lg:w-3/5 mx-auto">
    </div>
    <slot>
    </slot>
  </div>
</template>

<style scoped>
</style> 