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
  title: "My Barber",
  subtitle: "Dual-Interface Booking System",
  description:
    "Complete booking and management system for barber shops with dual user interfaces",
  image: "/projects/barbershop.png",
  liveUrl: "https://mybarberdev.my/",
  githubUrl: "https://github.com/fieck-san",
  technologies: [
    "React",
    "TypeScript",
    "Node.js",
    "Express.js",
    "MySQL",
    "Socket.io",
    "Stripe API",
  ],
  features: [
    "Business owner dashboard",
    "Customer booking interface",
    "Real-time availability",
    "Payment processing",
  ],
};

useSeoMeta({
  title: "My Barber",
  description:
    "Case study of the Barber Management App with dual-interface booking system",
});
</script>
