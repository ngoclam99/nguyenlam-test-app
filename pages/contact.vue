<script setup lang="ts">
import { ref } from 'vue'

// Meta tags
useHead({
  title: 'Liên hệ - My App',
  meta: [
    { name: 'description', content: 'Liên hệ với chúng tôi để được tư vấn' }
  ]
})

// Form data
interface ContactForm {
  name: string
  email: string
  phone: string
  subject: string
  message: string
}

const formData = ref<ContactForm>({
  name: '',
  email: '',
  phone: '',
  subject: '',
  message: ''
})

const isSubmitting = ref(false)
const submitSuccess = ref(false)

// Submit form
const handleSubmit = async () => {
  isSubmitting.value = true
  
  // Giả lập gửi form (thay bằng API thật)
  setTimeout(() => {
    console.log('Form data:', formData.value)
    isSubmitting.value = false
    submitSuccess.value = true
    
    // Reset form
    formData.value = {
      name: '',
      email: '',
      phone: '',
      subject: '',
      message: ''
    }
    
    // Ẩn thông báo sau 3 giây
    setTimeout(() => {
      submitSuccess.value = false
    }, 3000)
  }, 1500)
}

// Contact info
const contactInfo = [
  {
    icon: '📍',
    title: 'Địa chỉ',
    content: '123 Đường ABC, Quận 1, TP.HCM'
  },
  {
    icon: '📞',
    title: 'Điện thoại',
    content: '+84 123 456 789'
  },
  {
    icon: '📧',
    title: 'Email',
    content: 'contact@myapp.com'
  },
  {
    icon: '⏰',
    title: 'Giờ làm việc',
    content: 'T2 - T6: 9:00 - 18:00'
  }
]
</script>

<template>
  <div class="min-h-screen bg-gray-50">
    <!-- Header -->
    <AppHeader />

    <!-- Hero Section -->
    <section class="bg-gradient-to-r from-blue-600 to-indigo-700 py-20">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="max-w-3xl mx-auto text-center">
          <h1 class="text-4xl sm:text-5xl font-bold text-white mb-6">
            Liên hệ với chúng tôi
          </h1>
          <p class="text-xl text-blue-100 leading-relaxed">
            Chúng tôi luôn sẵn sàng lắng nghe và hỗ trợ bạn
          </p>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section class="py-20 bg-white">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid lg:grid-cols-2 gap-12">
          <!-- Contact Info -->
          <div>
            <h2 class="text-3xl font-bold text-gray-900 mb-8">
              Thông tin liên hệ
            </h2>
            
            <div class="space-y-6 mb-8">
              <div
                v-for="(info, index) in contactInfo"
                :key="index"
                class="flex items-start"
              >
                <div class="text-4xl mr-4">{{ info.icon }}</div>
                <div>
                  <h3 class="font-bold text-gray-900 mb-1">{{ info.title }}</h3>
                  <p class="text-gray-600">{{ info.content }}</p>
                </div>
              </div>
            </div>

            <!-- Map Placeholder -->
            <div class="bg-gray-200 rounded-xl h-64 flex items-center justify-center">
              <div class="text-center text-gray-500">
                <svg class="w-16 h-16 mx-auto mb-2" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17.657 16.657L13.414 20.9a1.998 1.998 0 01-2.827 0l-4.244-4.243a8 8 0 1111.314 0z" />
                  <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 11a3 3 0 11-6 0 3 3 0 016 0z" />
                </svg>
                <p>Google Maps</p>
              </div>
            </div>
          </div>

          <!-- Contact Form -->
          <div>
            <h2 class="text-3xl font-bold text-gray-900 mb-8">
              Gửi tin nhắn
            </h2>

            <!-- Success Message -->
            <div
              v-if="submitSuccess"
              class="bg-green-100 border border-green-400 text-green-700 px-4 py-3 rounded-lg mb-6"
            >
              ✓ Cảm ơn bạn! Chúng tôi sẽ liên hệ lại sớm nhất.
            </div>

            <form @submit.prevent="handleSubmit" class="space-y-6">
              <!-- Name -->
              <div>
                <label class="block text-gray-700 font-semibold mb-2">
                  Họ và tên *
                </label>
                <input
                  v-model="formData.name"
                  type="text"
                  required
                  class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent outline-none transition"
                  placeholder="Nguyễn Văn A"
                />
              </div>

              <!-- Email -->
              <div>
                <label class="block text-gray-700 font-semibold mb-2">
                  Email *
                </label>
                <input
                  v-model="formData.email"
                  type="email"
                  required
                  class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent outline-none transition"
                  placeholder="email@example.com"
                />
              </div>

              <!-- Phone -->
              <div>
                <label class="block text-gray-700 font-semibold mb-2">
                  Số điện thoại
                </label>
                <input
                  v-model="formData.phone"
                  type="tel"
                  class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent outline-none transition"
                  placeholder="0123456789"
                />
              </div>

              <!-- Subject -->
              <div>
                <label class="block text-gray-700 font-semibold mb-2">
                  Chủ đề *
                </label>
                <input
                  v-model="formData.subject"
                  type="text"
                  required
                  class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent outline-none transition"
                  placeholder="Tôi muốn tư vấn về..."
                />
              </div>

              <!-- Message -->
              <div>
                <label class="block text-gray-700 font-semibold mb-2">
                  Nội dung *
                </label>
                <textarea
                  v-model="formData.message"
                  required
                  rows="5"
                  class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-blue-500 focus:border-transparent outline-none transition resize-none"
                  placeholder="Nhập nội dung tin nhắn của bạn..."
                ></textarea>
              </div>

              <!-- Submit Button -->
              <button
                type="submit"
                :disabled="isSubmitting"
                class="w-full bg-blue-600 text-white py-4 rounded-lg hover:bg-blue-700 transition-colors duration-200 font-semibold disabled:bg-gray-400 disabled:cursor-not-allowed"
              >
                <span v-if="!isSubmitting">Gửi tin nhắn</span>
                <span v-else>Đang gửi...</span>
              </button>
            </form>
          </div>
        </div>
      </div>
    </section>

    <!-- Footer -->
    <AppFooter />
  </div>
</template>

