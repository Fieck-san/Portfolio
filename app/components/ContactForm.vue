<template>
  <section class="section-padding bg-white">
    <div class="container-custom">
      <div class="max-w-2xl mx-auto">
        <form @submit.prevent="submitForm" class="card p-8">
          <div class="grid grid-cols-1 md:grid-cols-2 gap-6 mb-6">
            <div>
              <label for="name" class="block text-sm font-medium text-gray-700 mb-2">
                Name *
              </label>
              <input
                id="name"
                v-model="form.name"
                type="text"
                required
                class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-primary-500 outline-none transition-colors"
                placeholder="Your full name"
              />
            </div>
            
            <div>
              <label for="email" class="block text-sm font-medium text-gray-700 mb-2">
                Email *
              </label>
              <input
                id="email"
                v-model="form.email"
                type="email"
                required
                class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-primary-500 outline-none transition-colors"
                placeholder="your.email@example.com"
              />
            </div>
          </div>
          
          <div class="mb-6">
            <label for="subject" class="block text-sm font-medium text-gray-700 mb-2">
              Subject *
            </label>
            <input
              id="subject"
              v-model="form.subject"
              type="text"
              required
              class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-primary-500 outline-none transition-colors"
              placeholder="Project inquiry, collaboration, etc."
            />
          </div>
          
          <div class="mb-6">
            <label for="message" class="block text-sm font-medium text-gray-700 mb-2">
              Message *
            </label>
            <textarea
              id="message"
              v-model="form.message"
              required
              rows="6"
              class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-primary-500 focus:border-primary-500 outline-none transition-colors resize-vertical"
              placeholder="Tell me about your project..."
            ></textarea>
          </div>
          
          <button 
            type="submit" 
            :disabled="isSubmitting"
            class="w-full btn-primary disabled:opacity-50 disabled:cursor-not-allowed"
          >
            <span v-if="!isSubmitting">Send Message</span>
            <span v-else>Sending...</span>
          </button>
          
          <p v-if="successMessage" class="mt-4 text-green-600 text-center">
            {{ successMessage }}
          </p>
          
          <p v-if="errorMessage" class="mt-4 text-red-600 text-center">
            {{ errorMessage }}
          </p>
        </form>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
const form = reactive({
  name: '',
  email: '',
  subject: '',
  message: ''
})

const isSubmitting = ref(false)
const successMessage = ref('')
const errorMessage = ref('')

const submitForm = async () => {
  isSubmitting.value = true
  successMessage.value = ''
  errorMessage.value = ''
  
  try {
    // TODO: Implement actual form submission
    await new Promise(resolve => setTimeout(resolve, 1000))
    
    successMessage.value = 'Message sent successfully! I\'ll get back to you soon.'
    
    // Reset form
    Object.assign(form, {
      name: '',
      email: '',
      subject: '',
      message: ''
    })
  } catch (error) {
    errorMessage.value = 'Failed to send message. Please try again.'
  } finally {
    isSubmitting.value = false
  }
}
</script>