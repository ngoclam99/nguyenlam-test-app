# HƯỚNG DẪN TẠO VÀ QUẢN LÝ TRANG TRONG NUXT 3

## 📁 Cấu trúc dự án hiện tại

```
my-app/
├── app.vue                    ← File gốc (Root Layout)
├── pages/                     ← Thư mục chứa các trang
│   ├── index.vue             ← Trang chủ (/)
│   ├── about.vue             ← Trang về chúng tôi (/about)
│   ├── services.vue          ← Trang dịch vụ (/services)
│   └── contact.vue           ← Trang liên hệ (/contact)
└── components/                ← Thư mục chứa components
    ├── AppHeader.vue         ← Header component
    ├── HeroSection.vue       ← Hero section component
    ├── FeaturesSection.vue   ← Features section component
    ├── CtaSection.vue        ← CTA section component
    └── AppFooter.vue         ← Footer component
```

## 🚀 Cách tạo một trang mới

### Bước 1: Tạo file trong thư mục `pages/`

Tạo file mới trong thư mục `pages/` với tên bạn muốn:

```
pages/
└── ten-trang.vue  → URL sẽ là: /ten-trang
```

### Bước 2: Cấu trúc cơ bản của một trang

```vue
<script setup lang="ts">
// 1. Import các thư viện cần thiết
import { ref } from 'vue'

// 2. Định nghĩa meta tags cho SEO
useHead({
  title: 'Tiêu đề trang - My App',
  meta: [
    { name: 'description', content: 'Mô tả trang của bạn' }
  ]
})

// 3. Định nghĩa interfaces (nếu cần)
interface DataType {
  id: number
  name: string
}

// 4. Khai báo dữ liệu
const data = ref<DataType[]>([
  { id: 1, name: 'Item 1' },
  { id: 2, name: 'Item 2' }
])

// 5. Khai báo functions
const handleClick = () => {
  console.log('Clicked!')
}
</script>

<template>
  <div class="min-h-screen bg-gray-50">
    <!-- Header -->
    <AppHeader />

    <!-- Nội dung trang của bạn -->
    <section class="py-20">
      <div class="container mx-auto px-4">
        <h1 class="text-4xl font-bold">Tiêu đề trang</h1>
        <!-- Thêm nội dung ở đây -->
      </div>
    </section>

    <!-- Footer -->
    <AppFooter />
  </div>
</template>
```

## 📋 Các trang đã tạo

### 1. Trang chủ - `pages/index.vue`
- **URL**: `/` hoặc `http://localhost:3000/`
- **Nội dung**: 
  - Hero section với CTA buttons
  - Features section (6 tính năng)
  - CTA section
- **Components sử dụng**: AppHeader, HeroSection, FeaturesSection, CtaSection, AppFooter

### 2. Trang về chúng tôi - `pages/about.vue`
- **URL**: `/about` hoặc `http://localhost:3000/about`
- **Nội dung**: Thông tin về công ty
- **Components sử dụng**: AppHeader, About, AppFooter

### 3. Trang dịch vụ - `pages/services.vue`
- **URL**: `/services` hoặc `http://localhost:3000/services`
- **Nội dung**:
  - Hero section
  - 6 dịch vụ với giá và tính năng
  - Quy trình làm việc (4 bước)
  - CTA section
- **Dữ liệu**: Array của 6 services với icon, title, description, features, price

### 4. Trang liên hệ - `pages/contact.vue`
- **URL**: `/contact` hoặc `http://localhost:3000/contact`
- **Nội dung**:
  - Thông tin liên hệ (địa chỉ, phone, email, giờ làm việc)
  - Form liên hệ với validation
  - Google Maps placeholder
- **Tính năng**: Form submit với loading state và success message

## 🎯 Routing tự động của Nuxt

Nuxt 3 tự động tạo routes dựa trên cấu trúc thư mục `pages/`:

```
pages/index.vue           → /
pages/about.vue           → /about
pages/services.vue        → /services
pages/contact.vue         → /contact
pages/blog/index.vue      → /blog
pages/blog/[id].vue       → /blog/:id (dynamic route)
pages/user/[id]/edit.vue  → /user/:id/edit
```

## 🔗 Cách điều hướng giữa các trang

### 1. Sử dụng `<NuxtLink>`

```vue
<template>
  <!-- Cách 1: Dùng to prop -->
  <NuxtLink to="/">Trang chủ</NuxtLink>
  <NuxtLink to="/about">Về chúng tôi</NuxtLink>
  <NuxtLink to="/services">Dịch vụ</NuxtLink>
  <NuxtLink to="/contact">Liên hệ</NuxtLink>

  <!-- Cách 2: Dùng :to với object -->
  <NuxtLink :to="{ path: '/about' }">Về chúng tôi</NuxtLink>
  
  <!-- Cách 3: Với query params -->
  <NuxtLink :to="{ path: '/services', query: { category: 'web' } }">
    Dịch vụ Web
  </NuxtLink>
</template>
```

### 2. Sử dụng `navigateTo()` trong code

```vue
<script setup lang="ts">
const goToAbout = () => {
  navigateTo('/about')
}

const goToServiceWithParams = () => {
  navigateTo({
    path: '/services',
    query: { id: 123 }
  })
}
</script>

<template>
  <button @click="goToAbout">Đi đến About</button>
</template>
```

## 📝 Ví dụ: Tạo trang Blog

### Tạo file `pages/blog.vue`

```vue
<script setup lang="ts">
useHead({
  title: 'Blog - My App',
  meta: [
    { name: 'description', content: 'Các bài viết mới nhất' }
  ]
})

interface Post {
  id: number
  title: string
  excerpt: string
  date: string
}

const posts: Post[] = [
  {
    id: 1,
    title: 'Bài viết 1',
    excerpt: 'Mô tả ngắn...',
    date: '2024-01-01'
  }
]
</script>

<template>
  <div class="min-h-screen bg-gray-50">
    <AppHeader />
    
    <section class="py-20">
      <div class="container mx-auto px-4">
        <h1 class="text-4xl font-bold mb-8">Blog</h1>
        
        <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div
            v-for="post in posts"
            :key="post.id"
            class="bg-white rounded-lg p-6 shadow-md"
          >
            <h2 class="text-xl font-bold mb-2">{{ post.title }}</h2>
            <p class="text-gray-600 mb-4">{{ post.excerpt }}</p>
            <NuxtLink
              :to="`/blog/${post.id}`"
              class="text-blue-600 hover:underline"
            >
              Đọc thêm →
            </NuxtLink>
          </div>
        </div>
      </div>
    </section>
    
    <AppFooter />
  </div>
</template>
```

## 🎨 Tùy chỉnh Layout

### Tạo layout riêng (nếu cần)

Tạo file `layouts/custom.vue`:

```vue
<template>
  <div>
    <header>Custom Header</header>
    <slot />
    <footer>Custom Footer</footer>
  </div>
</template>
```

Sử dụng trong trang:

```vue
<script setup lang="ts">
definePageMeta({
  layout: 'custom'
})
</script>
```

## ✅ Checklist khi tạo trang mới

- [ ] Tạo file `.vue` trong thư mục `pages/`
- [ ] Thêm `useHead()` cho SEO
- [ ] Thêm `<AppHeader />` ở đầu
- [ ] Thêm `<AppFooter />` ở cuối
- [ ] Định nghĩa TypeScript interfaces cho dữ liệu
- [ ] Thêm responsive classes (sm:, md:, lg:)
- [ ] Test trên mobile và desktop
- [ ] Cập nhật menu trong `AppHeader.vue` (nếu cần)

## 🚀 Chạy dự án

```bash
# Development
npm run dev

# Build
npm run build

# Preview production build
npm run preview
```

Truy cập: `http://localhost:3000`

## 📚 Tài liệu tham khảo

- Nuxt 3 Routing: https://nuxt.com/docs/getting-started/routing
- Nuxt 3 Pages: https://nuxt.com/docs/guide/directory-structure/pages
- Vue 3 Composition API: https://vuejs.org/guide/extras/composition-api-faq.html

