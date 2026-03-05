<script setup lang="ts">
const currentYear = new Date().getFullYear()

const footerLinks = {
  product: [
    { name: 'Tính năng', href: '/features' },
    { name: 'Giá cả', href: '/pricing' },
    { name: 'Tài liệu', href: '/docs' },
    { name: 'API', href: '/api' }
  ],
  company: [
    { name: 'Về chúng tôi', href: '/about' },
    { name: 'Blog', href: '/blog' },
    { name: 'Tuyển dụng', href: '/careers' },
    { name: 'Liên hệ', href: '/contact' }
  ],
  legal: [
    { name: 'Chính sách bảo mật', href: '/privacy' },
    { name: 'Điều khoản sử dụng', href: '/terms' },
    { name: 'Cookie', href: '/cookies' }
  ]
}

const socialLinks = [
  { name: 'Facebook', icon: 'M24 12.073c0-6.627-5.373-12-12-12s-12 5.373-12 12c0 5.99 4.388 10.954 10.125 11.854v-8.385H7.078v-3.47h3.047V9.43c0-3.007 1.792-4.669 4.533-4.669 1.312 0 2.686.235 2.686.235v2.953H15.83c-1.491 0-1.956.925-1.956 1.874v2.25h3.328l-.532 3.47h-2.796v8.385C19.612 23.027 24 18.062 24 12.073z' },
  { name: 'Twitter', icon: 'M23.953 4.57a10 10 0 01-2.825.775 4.958 4.958 0 002.163-2.723c-.951.555-2.005.959-3.127 1.184a4.92 4.92 0 00-8.384 4.482C7.69 8.095 4.067 6.13 1.64 3.162a4.822 4.822 0 00-.666 2.475c0 1.71.87 3.213 2.188 4.096a4.904 4.904 0 01-2.228-.616v.06a4.923 4.923 0 003.946 4.827 4.996 4.996 0 01-2.212.085 4.936 4.936 0 004.604 3.417 9.867 9.867 0 01-6.102 2.105c-.39 0-.779-.023-1.17-.067a13.995 13.995 0 007.557 2.209c9.053 0 13.998-7.496 13.998-13.985 0-.21 0-.42-.015-.63A9.935 9.935 0 0024 4.59z' },
  { name: 'GitHub', icon: 'M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z' }
]
</script>

<template>
  <footer class="bg-gray-900 text-gray-300">
    <div class="container mx-auto px-4 sm:px-6 lg:px-8 py-12">
      <!-- Main Footer Content -->
      <div class="grid md:grid-cols-2 lg:grid-cols-4 gap-8 mb-8">
        <!-- Brand -->
        <div>
          <h3 class="text-white text-2xl font-bold mb-4">MyApp</h3>
          <p class="text-gray-400 mb-4">
            Xây dựng ứng dụng web hiện đại với công nghệ tốt nhất.
          </p>
          <!-- Social Links -->
          <div class="flex space-x-4">
            <a
              v-for="social in socialLinks"
              :key="social.name"
              href="#"
              class="text-gray-400 hover:text-white transition-colors duration-200"
              :aria-label="social.name"
            >
              <svg class="w-6 h-6" fill="currentColor" viewBox="0 0 24 24">
                <path :d="social.icon" />
              </svg>
            </a>
          </div>
        </div>

        <!-- Product Links -->
        <div>
          <h4 class="text-white font-semibold mb-4">Sản phẩm</h4>
          <ul class="space-y-2">
            <li v-for="link in footerLinks.product" :key="link.name">
              <NuxtLink :to="link.href" class="hover:text-white transition-colors duration-200">
                {{ link.name }}
              </NuxtLink>
            </li>
          </ul>
        </div>

        <!-- Company Links -->
        <div>
          <h4 class="text-white font-semibold mb-4">Công ty</h4>
          <ul class="space-y-2">
            <li v-for="link in footerLinks.company" :key="link.name">
              <NuxtLink :to="link.href" class="hover:text-white transition-colors duration-200">
                {{ link.name }}
              </NuxtLink>
            </li>
          </ul>
        </div>

        <!-- Legal Links -->
        <div>
          <h4 class="text-white font-semibold mb-4">Pháp lý</h4>
          <ul class="space-y-2">
            <li v-for="link in footerLinks.legal" :key="link.name">
              <NuxtLink :to="link.href" class="hover:text-white transition-colors duration-200">
                {{ link.name }}
              </NuxtLink>
            </li>
          </ul>
        </div>
      </div>

      <!-- Bottom Bar -->
      <div class="border-t border-gray-800 pt-8">
        <p class="text-center text-gray-400">
          © {{ currentYear }} MyApp. Tất cả quyền được bảo lưu.
        </p>
      </div>
    </div>
  </footer>
</template>

