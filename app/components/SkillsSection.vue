<template>
  <section class="section-padding bg-gray-50">
    <div class="container-custom">
      <div class="text-center mb-16">
        <h2 class="text-3xl lg:text-4xl font-bold text-gray-900 mb-4">
          Skills & Technologies
        </h2>
        <p class="text-lg text-gray-600 max-w-2xl mx-auto">
          A comprehensive toolkit for building modern web applications
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="category in skillCategories"
          :key="category.title"
          class="card p-6"
        >
          <h3 class="text-xl font-semibold text-gray-900 mb-4">
            {{ category.title }}
          </h3>
          <div class="flex flex-wrap gap-2">
            <span
              v-for="skill in category.skills"
              :key="skill"
              class="px-3 py-1 bg-primary-100 text-primary-700 text-sm font-medium rounded-full"
            >
              {{ skill }}
            </span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const skillCategories = [
  {
    title: "Frontend",
    skills: [
      "Vue.js",
      "Nuxt",
      "React",
      "Next.js",
      "TypeScript",
      "Tailwind CSS",
      "PHP",
      "HTML",
      "CSS",
      "Javascript",
      "TypeScript",
      "Bootstrap",
    ],
  },
  {
    title: "Backend",
    skills: [
      "Node.js",
      "Laravel",
      "Prisma",
      "Java",
      "Javascript",
      "mySQL",
      "Supabase",
      "phpMyAdmin",
      "PHP",
      "Rest API",
      "CouchDB",
    ],
  },
  {
    title: "Tools & Others",
    skills: [
      "Git",
      "Gitlab",
      "Github",
      "Docker",
      "Adobe XD",
      "Ollama",
      "Figma",
      "VS Code",
      "AWS",
    ],
  },
];
</script>
