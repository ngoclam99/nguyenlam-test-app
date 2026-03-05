<script setup lang="ts">
interface Feature {
  icon: string
  title: string
  description: string
}

const features: Feature[] = [
  {
    icon: '⚡',
    title: 'Hiệu suất cao',
    description: 'Tối ưu hóa tốc độ tải trang và trải nghiệm người dùng với Nuxt 3.'
  },
  {
    icon: '🎨',
    title: 'Thiết kế đẹp',
    description: 'Giao diện hiện đại và responsive với Tailwind CSS.'
  },
  {
    icon: '🔒',
    title: 'Bảo mật',
    description: 'Các tính năng bảo mật tích hợp sẵn để bảo vệ ứng dụng của bạn.'
  },
  {
    icon: '📱',
    title: 'Responsive',
    description: 'Hoạt động mượt mà trên mọi thiết bị và kích thước màn hình.'
  },
  {
    icon: '🚀',
    title: 'SEO Friendly',
    description: 'Tối ưu hóa công cụ tìm kiếm với SSR và meta tags động.'
  },
  {
    icon: '💻',
    title: 'TypeScript',
    description: 'Type-safe với TypeScript để code chất lượng cao hơn.'
  }
]
</script>

<template>
  <section class="py-20 bg-white">
    <div class="container mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <h2 class="text-3xl sm:text-4xl lg:text-5xl font-bold text-gray-900 mb-4">
          Tính năng nổi bật
        </h2>
        <p class="text-lg text-gray-600 max-w-2xl mx-auto">
          Khám phá những tính năng mạnh mẽ giúp bạn xây dựng ứng dụng tốt hơn
        </p>
      </div>

      <!-- Features Grid -->
      <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="(feature, index) in features"
          :key="index"
          class="bg-gray-50 rounded-xl p-8 hover:shadow-lg transition-all duration-300 hover:-translate-y-1 border border-gray-100"
        >
          <div class="text-5xl mb-4">{{ feature.icon }}</div>
          <h3 class="text-xl font-bold text-gray-900 mb-3">
            {{ feature.title }}
          </h3>
          <p class="text-gray-600 leading-relaxed">
            {{ feature.description }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

