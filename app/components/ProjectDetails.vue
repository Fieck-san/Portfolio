<template>
  <section class="section-padding bg-white">
    <div class="container-custom">
      <div class="max-w-4xl mx-auto">
        <h2 class="text-3xl font-bold text-gray-900 mb-6">Project Overview</h2>
        <p class="text-lg text-gray-600 leading-relaxed">
          {{ project.description }}
        </p>
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