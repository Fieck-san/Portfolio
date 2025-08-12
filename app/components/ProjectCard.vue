<template>
  <div class="card card-hover group cursor-pointer overflow-hidden">
    <NuxtLink :to="`/projects/${project.slug}`" class="block">
      <div class="relative h-48 bg-gray-100 overflow-hidden">
        <img
          v-if="project.image"
          :src="project.image"
          :alt="project.title"
          class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-500"
        />
        <div
          v-else
          class="w-full h-full bg-gradient-to-br from-primary-500 to-primary-700 flex items-center justify-center"
        >
          <span class="text-white text-2xl font-bold">{{
            project.title.slice(0, 2)
          }}</span>
        </div>

        <div
          class="absolute inset-0 bg-black/0 group-hover:bg-black/10 transition-colors duration-300"
        ></div>
      </div>

      <div class="p-6">
        <h3
          class="text-xl font-semibold text-gray-900 mb-2 group-hover:text-primary-600 transition-colors"
        >
          {{ project.title }}
        </h3>

        <p class="text-gray-600 mb-4 line-clamp-2">
          {{ project.description }}
        </p>

        <div class="flex flex-wrap gap-2 mb-4">
          <span
            v-for="tech in project.technologies.slice(0, 3)"
            :key="tech"
            class="px-2 py-1 bg-gray-100 text-gray-700 text-xs font-medium rounded-full"
          >
            {{ tech }}
          </span>
          <span
            v-if="project.technologies.length > 3"
            class="px-2 py-1 bg-gray-100 text-gray-500 text-xs font-medium rounded-full"
          >
            +{{ project.technologies.length - 3 }} more
          </span>
        </div>

        <div
          class="flex items-center text-primary-600 font-medium group-hover:translate-x-1 transition-transform"
        >
          View Case Study
          <Icon name="arrow-right" class="ml-1 w-4 h-4" />
        </div>
      </div>
    </NuxtLink>
  </div>
</template>

<script setup lang="ts">
interface Project {
  id: number;
  title: string;
  description: string;
  image?: string;
  technologies: string[];
  slug: string;
  featured?: boolean;
}

defineProps<{
  project: Project;
}>();
</script>

<style scoped>
.line-clamp-2 {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
</style>
