<template>
  <section
    class="relative min-h-screen flex items-center justify-center bg-gradient-to-br from-gray-50 to-white overflow-hidden"
  >
    <div class="absolute inset-0 bg-grid-pattern opacity-5"></div>

    <div class="container-custom relative z-10">
      <div class="text-center">
        <div class="animate-fade-in">
          <h1 class="text-5xl lg:text-7xl font-bold text-gray-900 mb-6">
            Hello, I'm
            <span class="text-gradient">Your Name</span>
          </h1>

          <p class="text-xl lg:text-2xl text-gray-600 mb-4 max-w-3xl mx-auto">
            Frontend Engineer with Backend Capabilities
          </p>

          <p class="text-lg text-gray-500 mb-8 max-w-2xl mx-auto">
            I craft exceptional digital experiences through modern web
            technologies, combining beautiful user interfaces with robust
            backend solutions.
          </p>

          <div
            class="flex flex-col sm:flex-row gap-4 justify-center items-center"
          >
            <NuxtLink to="/projects" class="btn-primary">
              View My Work
            </NuxtLink>

            <NuxtLink to="/contact" class="btn-secondary">
              Get In Touch
            </NuxtLink>
          </div>
        </div>

        <div class="mt-16 animate-bounce-slow">
          <Icon name="arrow-down" class="mx-auto text-gray-400" :size="24" />
        </div>
      </div>
    </div>

    <div class="absolute bottom-0 left-0 w-full">
      <svg
        viewBox="0 0 1440 120"
        fill="none"
        xmlns="http://www.w3.org/2000/svg"
      >
        <path
          d="M0,32L48,37.3C96,43,192,53,288,58.7C384,64,480,64,576,58.7C672,53,768,43,864,42.7C960,43,1056,53,1152,58.7C1248,64,1344,64,1392,64L1440,64L1440,120L1392,120C1344,120,1248,120,1152,120C1056,120,960,120,864,120C768,120,672,120,576,120C480,120,384,120,288,120C192,120,96,120,48,120L0,120Z"
          fill="white"
        />
      </svg>
    </div>
  </section>
</template>

<script setup lang="ts">
// Add scroll indicator animation on mount
onMounted(() => {
  // Add parallax effect or other animations here if needed
});
</script>

<style scoped>
.bg-grid-pattern {
  background-image: radial-gradient(
    circle at 1px 1px,
    rgba(0, 0, 0, 0.15) 1px,
    transparent 0
  );
  background-size: 20px 20px;
}

@keyframes arrow-down {
  0%,
  20%,
  50%,
  80%,
  100% {
    transform: translateY(0);
  }
  40% {
    transform: translateY(10px);
  }
  60% {
    transform: translateY(5px);
  }
}

.animate-bounce-slow {
  animation: arrow-down 2s infinite;
}
</style>
