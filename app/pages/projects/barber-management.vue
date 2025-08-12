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
  title: 'Barber Management App',
  subtitle: 'Dual-Interface Booking System',
  description: 'Complete booking and management system for barber shops with dual user interfaces',
  image: '/projects/barber-management.jpg',
  liveUrl: 'https://barber-app.example.com',
  githubUrl: 'https://github.com/username/barber-management',
  technologies: [
    'React', 'TypeScript', 'Node.js', 'Express.js',
    'MySQL', 'Socket.io', 'Stripe API'
  ],
  features: [
    'Business owner dashboard',
    'Customer booking interface',
    'Real-time availability',
    'Payment processing'
  ]
}

useSeoMeta({
  title: 'Barber Management App - Project Case Study',
  description: 'Case study of the Barber Management App with dual-interface booking system',
})
</script>