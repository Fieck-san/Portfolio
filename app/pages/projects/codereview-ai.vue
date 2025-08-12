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
  title: 'CodeReview AI',
  subtitle: 'Intelligent Code Analysis Platform',
  description: 'AI-powered code review and analysis tool for development teams',
  image: '/projects/codereview-ai.jpg',
  liveUrl: 'https://codereview-ai.example.com',
  githubUrl: 'https://github.com/username/codereview-ai',
  technologies: [
    'Vue.js 3', 'TypeScript', 'Node.js', 'Express.js',
    'MongoDB', 'OpenAI API', 'Docker'
  ],
  features: [
    'Automated code review',
    'AI-powered suggestions',
    'Team collaboration tools'
  ]
}

useSeoMeta({
  title: 'CodeReview AI - Project Case Study',
  description: 'Explore CodeReview AI - intelligent code analysis platform',
})
</script>