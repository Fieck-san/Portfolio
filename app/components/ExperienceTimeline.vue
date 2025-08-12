<template>
  <section class="section-padding bg-white">
    <div class="container-custom">
      <div class="text-center mb-16">
        <h2 class="text-3xl lg:text-4xl font-bold text-gray-900 mb-4">
          Experience
        </h2>
        <p class="text-lg text-gray-600 max-w-2xl mx-auto">
          My journey in web development and technology
        </p>
      </div>

      <div class="max-w-4xl mx-auto">
        <div class="relative">
          <!-- Timeline line - hidden on mobile -->
          <div class="absolute left-8 top-0 bottom-0 w-px bg-gray-200 hidden md:block"></div>

          <div
            v-for="(item, index) in timeline"
            :key="index"
            class="relative flex flex-col md:flex-row md:items-start mb-8 last:mb-0"
          >
            <!-- Year badge -->
            <div
              class="flex-shrink-0 w-16 h-16 md:w-16 md:h-16 w-12 h-12 bg-primary-600 rounded-full flex items-center justify-center md:mr-6 mb-4 md:mb-0 mx-auto md:mx-0"
            >
              <span class="text-white font-semibold text-sm md:text-base">{{ item.year }}</span>
            </div>

            <!-- Content card -->
            <div class="flex-1 card p-4 md:p-6">
              <h3 class="text-lg md:text-xl font-semibold text-gray-900 mb-2">
                {{ item.title }}
              </h3>
              <p class="text-primary-600 font-medium mb-3 text-sm md:text-base">
                {{ item.company }}
              </p>
              <p class="text-gray-600 text-sm md:text-base leading-relaxed">
                {{ item.description }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const timeline = [
  {
    year: "2024",
    title: "UI/UX Developer",
    company: "Fiuu (Razer Merchant Services)",
    description:
      "Architected comprehensive design systems to solve UX challenges, led frontend modernization from legacy PHP/Vue to Nuxt 4.0 with TypeScript and atomic components, reduced bundle size from 40MB to 4MB, and developed full-stack applications with payment integration while establishing team development standards.",
  },
  {
    year: "2023",
    title: "Application Developer",
    company: "Singularity Aerotech Asia",
    description:
      "Developed high-performance web applications with Redis caching optimization (achieving 40ms query response times), designed client-facing features and led UI redesign initiatives using Figma, and automated IoT data collection systems with MQTT and Node-RED for real-time monitoring.",
  },
];
</script>
