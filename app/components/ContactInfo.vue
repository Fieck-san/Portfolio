<template>
  <section class="section-padding bg-gray-50">
    <div class="container-custom">
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8 text-center">
        <div class="card p-6">
          <Icon name="email" class="mx-auto mb-4 text-primary-600" size="32" />
          <h3 class="text-lg font-semibold text-gray-900 mb-2">Email</h3>
          <a href="mailto:your.email@example.com" class="text-gray-600 hover:text-primary-600 transition-colors">
            your.email@example.com
          </a>
        </div>
        
        <div class="card p-6">
          <Icon name="github" class="mx-auto mb-4 text-primary-600" size="32" />
          <h3 class="text-lg font-semibold text-gray-900 mb-2">GitHub</h3>
          <a href="#" class="text-gray-600 hover:text-primary-600 transition-colors">
            @yourusername
          </a>
        </div>
        
        <div class="card p-6">
          <Icon name="linkedin" class="mx-auto mb-4 text-primary-600" size="32" />
          <h3 class="text-lg font-semibold text-gray-900 mb-2">LinkedIn</h3>
          <a href="#" class="text-gray-600 hover:text-primary-600 transition-colors">
            /in/yourname
          </a>
        </div>
      </div>
    </div>
  </section>
</template>