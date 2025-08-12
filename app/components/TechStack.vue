<template>
  <section class="section-padding bg-gray-50">
    <div class="container-custom">
      <div class="max-w-4xl mx-auto text-center">
        <h2 class="text-3xl font-bold text-gray-900 mb-8">Technology Stack</h2>
        
        <div class="flex flex-wrap gap-3 justify-center">
          <span 
            v-for="tech in technologies" 
            :key="tech"
            class="px-4 py-2 bg-white border border-gray-200 text-gray-700 font-medium rounded-lg shadow-sm hover:shadow-md transition-shadow"
          >
            {{ tech }}
          </span>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
defineProps<{
  technologies: string[]
}>()
</script>