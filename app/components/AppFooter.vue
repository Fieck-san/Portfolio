<template>
  <footer class="bg-gray-900 text-white">
    <div class="container-custom py-16">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <div>
          <h3 class="text-xl font-bold mb-4">Portfolio</h3>
          <p class="text-gray-400 mb-4">
            Frontend Engineer with Backend Capabilities
          </p>
          <div class="flex space-x-4">
            <a
              href="#"
              class="text-gray-400 hover:text-white transition-colors"
              aria-label="GitHub"
            >
              <Icon name="github" class="w-5 h-5" />
            </a>
            <a
              href="#"
              class="text-gray-400 hover:text-white transition-colors"
              aria-label="LinkedIn"
            >
              <Icon name="linkedin" class="w-5 h-5" />
            </a>
          </div>
        </div>

        <div>
          <h4 class="font-semibold mb-4">Quick Links</h4>
          <ul class="space-y-2">
            <li>
              <NuxtLink
                to="/about"
                class="text-gray-400 hover:text-white transition-colors"
              >
                About
              </NuxtLink>
            </li>
            <li>
              <NuxtLink
                to="/projects"
                class="text-gray-400 hover:text-white transition-colors"
              >
                Projects
              </NuxtLink>
            </li>
            <li>
              <NuxtLink
                to="/contact"
                class="text-gray-400 hover:text-white transition-colors"
              >
                Contact
              </NuxtLink>
            </li>
          </ul>
        </div>

        <div>
          <h4 class="font-semibold mb-4">Featured Projects</h4>
          <ul class="space-y-2">
            <li>
              <NuxtLink
                to="/projects/taskflow-ai"
                class="text-gray-400 hover:text-white transition-colors"
              >
                TaskFlow AI
              </NuxtLink>
            </li>
            <li>
              <NuxtLink
                to="/projects/codereview-ai"
                class="text-gray-400 hover:text-white transition-colors"
              >
                CodeReview AI
              </NuxtLink>
            </li>
            <li>
              <NuxtLink
                to="/projects/barber-management"
                class="text-gray-400 hover:text-white transition-colors"
              >
                Barber Management
              </NuxtLink>
            </li>
          </ul>
        </div>
      </div>

      <div class="border-t border-gray-800 mt-12 pt-8 text-center">
        <p class="text-gray-400">
          © {{ currentYear }} Portfolio. Built with Nuxt 4 & Tailwind CSS.
        </p>
      </div>
    </div>
  </footer>
</template>

<script setup lang="ts">
const currentYear = new Date().getFullYear();
</script>
