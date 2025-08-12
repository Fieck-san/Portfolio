<template>
  <div class="min-h-screen pt-20">
    <ProjectHero :project="project" />
    <ProjectDetails :project="project" />
    <TechStack :technologies="project.technologies" />
    <ProjectFeatures :features="project.features" />
    <ProjectLinks :project="project" />
  </div>
</template>

<script setup lang="ts">
const project = {
  title: 'TaskFlow AI',
  subtitle: 'AI-Powered Project Management Dashboard',
  description: 'Enterprise-ready project management solution with AI capabilities',
  image: '/projects/taskflow-ai.jpg',
  liveUrl: 'https://taskflow-ai.example.com',
  githubUrl: 'https://github.com/username/taskflow-ai',
  technologies: [
    'Next.js 14', 'TypeScript', 'Tailwind CSS', 'Shadcn/UI',
    'Prisma ORM', 'PostgreSQL', 'Supabase', 'NextAuth.js'
  ],
  features: [
    'Core Project Management (CRUD, team collaboration)',
    'AI-Powered Features (coming soon)',
    'Enterprise-Ready capabilities'
  ]
}

useSeoMeta({
  title: 'TaskFlow AI - Project Case Study',
  description: 'Deep dive into TaskFlow AI - AI-powered project management dashboard',
})
</script>