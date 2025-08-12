<template>
  <header
    class="fixed top-0 left-0 right-0 z-50 bg-white/90 backdrop-blur-sm border-b border-gray-100"
  >
    <nav class="container-custom py-4 relative">
      <div class="flex items-center justify-between">
        <NuxtLink
          to="/"
          class="text-xl font-bold text-gray-900 hover:text-primary-600 transition-colors"
        >
          Fieck's Portfolio
        </NuxtLink>

        <div class="hidden md:flex items-center space-x-8">
          <NuxtLink
            to="/"
            class="nav-link"
            :class="{ 'nav-link-active': $route.path === '/' }"
          >
            Home
          </NuxtLink>
          <NuxtLink
            to="/about"
            class="nav-link"
            :class="{ 'nav-link-active': $route.path === '/about' }"
          >
            About
          </NuxtLink>
          <NuxtLink
            to="/projects"
            class="nav-link"
            :class="{ 'nav-link-active': $route.path.startsWith('/projects') }"
          >
            Projects
          </NuxtLink>
          <NuxtLink
            to="/contact"
            class="nav-link"
            :class="{ 'nav-link-active': $route.path === '/contact' }"
          >
            Contact
          </NuxtLink>
          <a href="#" class="btn-primary text-sm" @click="downloadResume">
            Download Resume
          </a>
        </div>

        <button
          @click="toggleMobileMenu"
          class="md:hidden p-2 rounded-lg hover:bg-gray-100 transition-colors"
          aria-label="Toggle mobile menu"
        >
          <Icon name="menu" v-if="!isMobileMenuOpen" />
          <Icon name="x" v-else />
        </button>
      </div>

      <Transition name="mobile-menu">
        <div
          v-if="isMobileMenuOpen"
          class="absolute top-full left-0 right-0 md:hidden bg-white/95 backdrop-blur-sm border-t border-gray-100 shadow-lg"
        >
          <div class="container-custom py-4">
            <div class="flex flex-col space-y-4">
              <NuxtLink to="/" class="nav-link-mobile" @click="closeMobileMenu">
                Home
              </NuxtLink>
              <NuxtLink
                to="/about"
                class="nav-link-mobile"
                @click="closeMobileMenu"
              >
                About
              </NuxtLink>
              <NuxtLink
                to="/projects"
                class="nav-link-mobile"
                @click="closeMobileMenu"
              >
                Projects
              </NuxtLink>
              <NuxtLink
                to="/contact"
                class="nav-link-mobile"
                @click="closeMobileMenu"
              >
                Contact
              </NuxtLink>
              <button
                @click="downloadResume"
                class="btn-primary text-sm text-left w-full"
              >
                Download Resume
              </button>
            </div>
          </div>
        </div>
      </Transition>
    </nav>
  </header>
</template>

<script setup lang="ts">
const isMobileMenuOpen = ref(false);

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value;
};

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false;
};

const downloadResume = () => {
  // TODO: Implement resume download
  console.log("Download resume");
};

onMounted(() => {
  // Close mobile menu when clicking outside
  document.addEventListener("click", (event) => {
    const header = document.querySelector("header");
    if (header && !header.contains(event.target as Node)) {
      isMobileMenuOpen.value = false;
    }
  });
});
</script>

<style scoped>
.nav-link {
  @apply text-gray-600 hover:text-primary-600 font-medium transition-colors duration-200;
}

.nav-link-active {
  @apply text-primary-600;
}

.nav-link-mobile {
  @apply text-gray-700 hover:text-primary-600 font-medium py-2 transition-colors duration-200;
}

.mobile-menu-enter-active,
.mobile-menu-leave-active {
  transition: all 0.3s ease;
}

.mobile-menu-enter-from,
.mobile-menu-leave-to {
  opacity: 0;
  transform: translateY(-10px);
}
</style>
