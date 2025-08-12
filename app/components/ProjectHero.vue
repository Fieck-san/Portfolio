<template>
  <section class="section-padding bg-gray-50">
    <div class="container-custom">
      <div class="max-w-4xl mx-auto text-center">
        <h1 class="text-4xl lg:text-5xl font-bold text-gray-900 mb-4">
          {{ project.title }}
        </h1>
        <p class="text-xl text-gray-600 mb-8">
          {{ project.subtitle }}
        </p>
        
        <div class="relative h-96 bg-white rounded-xl shadow-lg overflow-hidden mb-8">
          <img 
            v-if="project.image"
            :src="project.image" 
            :alt="project.title"
            class="w-full h-full object-contain"
          />
          <div v-else class="w-full h-full bg-gradient-to-br from-primary-500 to-primary-700 flex items-center justify-center">
            <span class="text-white text-4xl font-bold">{{ project.title }}</span>
          </div>
        </div>
        
        <div class="flex flex-wrap gap-4 justify-center">
          <a 
            v-if="project.liveUrl"
            :href="project.liveUrl" 
            target="_blank" 
            rel="noopener noreferrer"
            class="btn-primary"
          >
            View Live Demo
          </a>
          
          <a 
            v-if="project.githubUrl"
            :href="project.githubUrl" 
            target="_blank" 
            rel="noopener noreferrer"
            class="btn-secondary"
          >
            View Code
          </a>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
interface Project {
  title: string
  subtitle: string
  description: string
  image?: string
  liveUrl?: string
  githubUrl?: string
  technologies?: string[]
  features?: string[]
}

defineProps<{
  project: Project
}>()
</script>