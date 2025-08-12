<template>
  <section class="section-padding bg-gray-50">
    <div class="container-custom text-center">
      <h2 class="text-3xl font-bold text-gray-900 mb-8">Explore This Project</h2>
      
      <div class="flex flex-wrap gap-4 justify-center mb-8">
        <a 
          v-if="project.liveUrl"
          :href="project.liveUrl" 
          target="_blank" 
          rel="noopener noreferrer"
          class="btn-primary"
        >
          View Live Demo
          <Icon name="external-link" class="ml-2 w-4 h-4" />
        </a>
        
        <a 
          v-if="project.githubUrl"
          :href="project.githubUrl" 
          target="_blank" 
          rel="noopener noreferrer"
          class="btn-secondary"
        >
          View Source Code
          <Icon name="github" class="ml-2 w-4 h-4" />
        </a>
      </div>
      
      <div class="border-t border-gray-200 pt-8">
        <p class="text-gray-600 mb-4">Interested in working together?</p>
        <NuxtLink to="/contact" class="btn-primary">
          Get In Touch
        </NuxtLink>
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