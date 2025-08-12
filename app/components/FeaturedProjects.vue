<template>
  <section class="section-padding bg-white">
    <div class="container-custom">
      <div class="text-center mb-16">
        <h2 class="text-3xl lg:text-4xl font-bold text-gray-900 mb-4">
          Featured Projects
        </h2>
        <p class="text-lg text-gray-600 max-w-2xl mx-auto">
          A showcase of my recent work in full-stack development, highlighting
          both frontend excellence and backend capabilities.
        </p>
      </div>

      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <ProjectCard
          v-for="project in featuredProjects"
          :key="project.id"
          :project="project"
          class="animate-slide-up"
        />
      </div>

      <div class="text-center mt-12">
        <NuxtLink to="/projects" class="btn-secondary">
          View All Projects
        </NuxtLink>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const featuredProjects = [
  {
    id: 1,
    title: "TaskFlow AI",
    description:
      "AI-powered project management dashboard with enterprise-ready capabilities and modern UI.",
    image: "/projects/taskflowai.png",
    technologies: ["Next.js 14", "TypeScript", "Tailwind CSS", "Supabase"],
    slug: "taskflow-ai",
    featured: true,
  },
  {
    id: 2,
    title: "CodeReview AI",
    description:
      "Intelligent code analysis platform with AI-powered suggestions and team collaboration.",
    image: "/projects/codereview.png",
    technologies: ["Vue.js 3", "Node.js", "MongoDB", "OpenAI API"],
    slug: "codereview-ai",
    featured: true,
  },
  {
    id: 3,
    title: "Barber Management App",
    description:
      "Complete booking system with dual interfaces for businesses and customers.",
    image: "/projects/barbershop.png",
    technologies: ["React", "Express.js", "MySQL", "Stripe API"],
    slug: "barber-management",
    featured: true,
  },
];
</script>
