<template>
  <section class="section-padding bg-white">
    <div class="container-custom">
      <div class="flex flex-wrap gap-4 mb-8 justify-center">
        <button
          v-for="filter in filters"
          :key="filter"
          @click="activeFilter = filter"
          :class="[
            'px-4 py-2 rounded-lg font-medium transition-colors',
            activeFilter === filter
              ? 'bg-primary-600 text-white'
              : 'bg-gray-100 text-gray-700 hover:bg-gray-200',
          ]"
        >
          {{ filter }}
        </button>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <ProjectCard
          v-for="project in filteredProjects"
          :key="project.id"
          :project="project"
          class="animate-slide-up"
        />
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const activeFilter = ref("All");

const filters = ["All", "Web Apps", "AI Projects", "Full Stack"];

const allProjects = [
  {
    id: 1,
    title: "TaskFlow AI",
    description:
      "AI-powered project management dashboard with enterprise-ready capabilities and modern UI.",
    image: "/projects/taskflowai.png",
    technologies: ["Next.js 14", "TypeScript", "Tailwind CSS", "Supabase"],
    slug: "taskflow-ai",
    category: "AI Projects",
  },
  {
    id: 2,
    title: "CodeReview AI",
    description:
      "Intelligent code analysis platform with AI-powered suggestions and team collaboration.",
    image: "/projects/codereview.png",
    technologies: ["Vue.js 3", "Node.js", "MongoDB", "OpenAI API"],
    slug: "codereview-ai",
    category: "AI Projects",
  },
  {
    id: 3,
    title: "My Barber",
    description:
      "Complete booking system with dual interfaces for businesses and customers.",
    image: "/projects/barbershop.png",
    technologies: ["React", "Express.js", "MySQL", "Stripe API"],
    slug: "barber-management",
    category: "Web Apps",
  },
];

const filteredProjects = computed(() => {
  if (activeFilter.value === "All") {
    return allProjects;
  }
  return allProjects.filter(
    (project) => project.category === activeFilter.value
  );
});
</script>
