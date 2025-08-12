<template>
  <section class="section-padding bg-white">
    <div class="container-custom">
      <div class="max-w-4xl mx-auto">
        <h2 class="text-3xl font-bold text-gray-900 mb-8 text-center">Key Features</h2>
        
        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
          <div 
            v-for="(feature, index) in features" 
            :key="index"
            class="flex items-start"
          >
            <div class="flex-shrink-0 w-8 h-8 bg-primary-600 rounded-full flex items-center justify-center mr-4 mt-1">
              <span class="text-white text-sm font-bold">{{ index + 1 }}</span>
            </div>
            <div>
              <p class="text-gray-700 font-medium">{{ feature }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
defineProps<{
  features: string[]
}>()
</script>