<script setup lang="ts">
// Meta tags cho SEO
useHead({
  title: 'Dịch vụ - My App',
  meta: [
    { name: 'description', content: 'Các dịch vụ chuyên nghiệp của chúng tôi' }
  ]
})

// Interface cho Service
interface Service {
  icon: string
  title: string
  description: string
  features: string[]
  price: string
}

// Dữ liệu các dịch vụ
const services: Service[] = [
  {
    icon: '🎨',
    title: 'Thiết kế UI/UX',
    description: 'Thiết kế giao diện đẹp mắt, trải nghiệm người dùng tối ưu',
    features: [
      'Nghiên cứu người dùng',
      'Wireframe & Prototype',
      'Design System',
      'Responsive Design'
    ],
    price: 'Từ 10.000.000đ'
  },
  {
    icon: '💻',
    title: 'Phát triển Web',
    description: 'Xây dựng website hiện đại với công nghệ mới nhất',
    features: [
      'Frontend Development',
      'Backend Development',
      'API Integration',
      'Database Design'
    ],
    price: 'Từ 20.000.000đ'
  },
  {
    icon: '📱',
    title: 'Phát triển Mobile',
    description: 'Ứng dụng di động cho iOS và Android',
    features: [
      'Native App Development',
      'Cross-platform (React Native)',
      'App Store Deployment',
      'Maintenance & Support'
    ],
    price: 'Từ 30.000.000đ'
  },
  {
    icon: '☁️',
    title: 'Cloud & DevOps',
    description: 'Triển khai và quản lý hạ tầng cloud',
    features: [
      'AWS/Azure/GCP Setup',
      'CI/CD Pipeline',
      'Monitoring & Logging',
      'Security & Backup'
    ],
    price: 'Từ 15.000.000đ'
  },
  {
    icon: '🔍',
    title: 'SEO & Marketing',
    description: 'Tối ưu hóa công cụ tìm kiếm và marketing',
    features: [
      'On-page SEO',
      'Technical SEO',
      'Content Strategy',
      'Analytics & Reporting'
    ],
    price: 'Từ 8.000.000đ'
  },
  {
    icon: '🛡️',
    title: 'Bảo mật & Tư vấn',
    description: 'Đảm bảo an toàn cho hệ thống của bạn',
    features: [
      'Security Audit',
      'Penetration Testing',
      'Code Review',
      'Compliance Consulting'
    ],
    price: 'Từ 12.000.000đ'
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
            Dịch vụ của chúng tôi
          </h1>
          <p class="text-xl text-blue-100 leading-relaxed">
            Giải pháp toàn diện cho mọi nhu cầu công nghệ của doanh nghiệp bạn
          </p>
        </div>
      </div>
    </section>

    <!-- Services Grid -->
    <section class="py-20 bg-white">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div
            v-for="(service, index) in services"
            :key="index"
            class="bg-white rounded-xl p-8 border-2 border-gray-100 hover:border-blue-500 hover:shadow-xl transition-all duration-300 hover:-translate-y-1"
          >
            <!-- Icon -->
            <div class="text-5xl mb-4">{{ service.icon }}</div>
            
            <!-- Title -->
            <h3 class="text-2xl font-bold text-gray-900 mb-3">
              {{ service.title }}
            </h3>
            
            <!-- Description -->
            <p class="text-gray-600 mb-6">
              {{ service.description }}
            </p>
            
            <!-- Features List -->
            <ul class="space-y-2 mb-6">
              <li
                v-for="(feature, idx) in service.features"
                :key="idx"
                class="flex items-start text-gray-700"
              >
                <svg class="w-5 h-5 text-green-500 mr-2 mt-0.5 flex-shrink-0" fill="currentColor" viewBox="0 0 20 20">
                  <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd" />
                </svg>
                <span class="text-sm">{{ feature }}</span>
              </li>
            </ul>
            
            <!-- Price -->
            <div class="border-t pt-4">
              <p class="text-blue-600 font-bold text-lg mb-4">
                {{ service.price }}
              </p>
              <button class="w-full bg-blue-600 text-white py-3 rounded-lg hover:bg-blue-700 transition-colors duration-200 font-semibold">
                Liên hệ ngay
              </button>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Process Section -->
    <section class="py-20 bg-gray-50">
      <div class="container mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-16">
          <h2 class="text-3xl sm:text-4xl font-bold text-gray-900 mb-4">
            Quy trình làm việc
          </h2>
          <p class="text-lg text-gray-600 max-w-2xl mx-auto">
            Chúng tôi tuân theo quy trình chuyên nghiệp để đảm bảo chất lượng dự án
          </p>
        </div>

        <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div class="text-center">
            <div class="bg-blue-100 w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4">
              <span class="text-2xl font-bold text-blue-600">1</span>
            </div>
            <h3 class="text-xl font-bold text-gray-900 mb-2">Tư vấn</h3>
            <p class="text-gray-600">Lắng nghe và phân tích yêu cầu của bạn</p>
          </div>

          <div class="text-center">
            <div class="bg-blue-100 w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4">
              <span class="text-2xl font-bold text-blue-600">2</span>
            </div>
            <h3 class="text-xl font-bold text-gray-900 mb-2">Lập kế hoạch</h3>
            <p class="text-gray-600">Xây dựng roadmap và timeline chi tiết</p>
          </div>

          <div class="text-center">
            <div class="bg-blue-100 w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4">
              <span class="text-2xl font-bold text-blue-600">3</span>
            </div>
            <h3 class="text-xl font-bold text-gray-900 mb-2">Thực hiện</h3>
            <p class="text-gray-600">Phát triển và kiểm thử sản phẩm</p>
          </div>

          <div class="text-center">
            <div class="bg-blue-100 w-16 h-16 rounded-full flex items-center justify-center mx-auto mb-4">
              <span class="text-2xl font-bold text-blue-600">4</span>
            </div>
            <h3 class="text-xl font-bold text-gray-900 mb-2">Bàn giao</h3>
            <p class="text-gray-600">Triển khai và hỗ trợ sau bàn giao</p>
          </div>
        </div>
      </div>
    </section>

    <!-- CTA Section -->
    <CtaSection />

    <!-- Footer -->
    <AppFooter />
  </div>
</template>

