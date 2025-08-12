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
          class="md:hidden p-2 rounded-lg hover:bg-gray-100 transition-colors flex items-center justify-center w-10 h-10"
          aria-label="Toggle mobile menu"
        >
          <Icon name="menu" v-if="!isMobileMenuOpen" class="pointer-events-none" />
          <Icon name="x" v-else class="pointer-events-none" />
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

const downloadResume = async () => {
  try {
    const resumeUrl = "/Resume.pdf";
    const fileName = "Resume.pdf";

    // Check if the file was partially downloaded before
    const partialData = localStorage.getItem("resume_partial_data");
    const partialSize = partialData
      ? parseInt(localStorage.getItem("resume_partial_size") || "0")
      : 0;

    // Create headers for resumable download
    const headers: HeadersInit = {};
    if (partialSize > 0) {
      headers["Range"] = `bytes=${partialSize}-`;
    }

    // Fetch the file with range header for resume support
    const response = await fetch(resumeUrl, { headers });

    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }

    // Handle partial content (206) or full content (200)
    let finalBlob: Blob;

    if (response.status === 206 && partialData) {
      // Resume download - combine partial data with new data
      const newData = await response.arrayBuffer();
      const existingData = new Uint8Array(Buffer.from(partialData, "base64"));
      const combined = new Uint8Array(existingData.length + newData.byteLength);
      combined.set(existingData);
      combined.set(new Uint8Array(newData), existingData.length);
      finalBlob = new Blob([combined], { type: "application/pdf" });

      // Clear partial data since download is complete
      localStorage.removeItem("resume_partial_data");
      localStorage.removeItem("resume_partial_size");
    } else {
      // Full download
      const arrayBuffer = await response.arrayBuffer();
      finalBlob = new Blob([arrayBuffer], { type: "application/pdf" });
    }

    // Create download link
    const url = window.URL.createObjectURL(finalBlob);
    const link = document.createElement("a");
    link.href = url;
    link.download = fileName;
    link.style.display = "none";

    document.body.appendChild(link);
    link.click();
    document.body.removeChild(link);

    // Clean up the object URL
    window.URL.revokeObjectURL(url);

    console.log("Resume downloaded successfully");
  } catch (error) {
    console.error("Download failed:", error);

    // In case of failure, try to save partial data for resume capability
    try {
      const partialResponse = await fetch("/resume.pdf");
      if (partialResponse.ok) {
        const partialData = await partialResponse.arrayBuffer();
        const base64Data = Buffer.from(partialData).toString("base64");
        localStorage.setItem("resume_partial_data", base64Data);
        localStorage.setItem(
          "resume_partial_size",
          partialData.byteLength.toString()
        );
        console.log("Partial data saved for resume capability");
      }
    } catch (saveError) {
      console.error("Failed to save partial data:", saveError);
    }

    alert("Download failed. Please try again.");
  }
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
