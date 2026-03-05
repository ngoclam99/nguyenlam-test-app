<script setup lang="ts">
// Hero section component
</script>

<template>
  <section class="bg-gradient-to-br from-blue-50 to-indigo-100 py-20 lg:py-32">
    <div class="container mx-auto px-4 sm:px-6 lg:px-8">
      <div class="grid lg:grid-cols-2 gap-12 items-center">
        <!-- Left Content -->
        <div class="text-center lg:text-left">
          <h1 class="text-4xl sm:text-5xl lg:text-6xl font-bold text-gray-900 mb-6 leading-tight">
            Xây dựng ứng dụng
            <span class="text-blue-600">tuyệt vời</span>
            với Nuxt 3
          </h1>
          <p class="text-lg sm:text-xl text-gray-600 mb-8 leading-relaxed">
            Tạo các ứng dụng web hiện đại, nhanh chóng và mạnh mẽ với Nuxt 3, TypeScript và Tailwind CSS.
          </p>
          <div class="flex flex-col sm:flex-row gap-4 justify-center lg:justify-start">
            <button class="bg-blue-600 text-white px-8 py-4 rounded-lg hover:bg-blue-700 transition-all duration-200 font-semibold shadow-lg hover:shadow-xl transform hover:-translate-y-0.5">
              Bắt đầu ngay
            </button>
            <button class="bg-white text-blue-600 px-8 py-4 rounded-lg hover:bg-gray-50 transition-all duration-200 font-semibold border-2 border-blue-600">
              Tìm hiểu thêm
            </button>
          </div>
        </div>

        <!-- Right Content - Placeholder Image -->
        <div class="relative">
          <div class="bg-gradient-to-br from-blue-400 to-indigo-600 rounded-2xl shadow-2xl aspect-square lg:aspect-auto lg:h-96 flex items-center justify-center">
            <svg class="w-32 h-32 text-white opacity-50" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 16l4.586-4.586a2 2 0 012.828 0L16 16m-2-2l1.586-1.586a2 2 0 012.828 0L20 14m-6-6h.01M6 20h12a2 2 0 002-2V6a2 2 0 00-2-2H6a2 2 0 00-2 2v12a2 2 0 002 2z" />
            </svg>
          </div>
          <!-- Decorative Elements -->
          <div class="absolute -top-4 -right-4 w-24 h-24 bg-yellow-400 rounded-full opacity-20 blur-xl"></div>
          <div class="absolute -bottom-4 -left-4 w-32 h-32 bg-pink-400 rounded-full opacity-20 blur-xl"></div>
        </div>
      </div>
    </div>
  </section>
</template>

