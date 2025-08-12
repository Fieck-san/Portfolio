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
  title: "CodeReview AI",
  subtitle: "Intelligent Code Analysis Platform (In Development)",
  description: "AI-powered code review and analysis tool for development teams - currently under active development with exciting features coming soon",
  image: "/projects/codereview.png",
  liveUrl: "",
  githubUrl: "https://github.com/username/codereview-ai",
  technologies: [
    "Vue.js 3",
    "TypeScript",
    "Node.js",
    "Express.js",
    "MongoDB",
    "OpenAI API",
    "Docker",
  ],
  features: [
    "Automated code review (In Progress)",
    "AI-powered suggestions (Coming Soon)",
    "Team collaboration tools (Planned)",
    "Real-time code analysis (In Development)",
  ],
};

useSeoMeta({
  title: "CodeReview AI - Project Case Study",
  description: "Explore CodeReview AI - intelligent code analysis platform",
});
</script>
